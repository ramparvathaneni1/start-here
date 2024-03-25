# Modern Engineering Fundamentals

## Getting Started


# Class Schedules

|          | Week 1                    | Week 2                    | Week 3                    | Week 4                    |
| -------- | ------------------------- | ------------------------- | ------------------------- | ------------------------- |
| Schedule | [View Schedule](./resources/week1.md) | [View Schedule](./resources/week2.md) | [View Schedule](./resources/week3.md) | [View Schedule](./resources/week4.md) |

## Deliverables

|          | [Build Your own API](https://git.generalassemb.ly/ModernEngineering/pru-individual-in-class-app)                    | [Build Your Own Full Stack Application](https://git.generalassemb.ly/ModernEngineering/pru-individual-in-class-app-react-frontend)                   | [Selenium Testing Lab](https://git.generalassemb.ly/ModernEngineering/add-selenium-to-personal-application)                    | [Dockerizing an Application](https://git.generalassemb.ly/ModernEngineering/docker-lab)                    |
| -------- | ------------------------- | ------------------------- | ------------------------- | ------------------------- |


<br>

## FAQ:

## Fork and Clone lessons/labs

1. On the top right corner of the repository, click the Fork button.

   ![](./assets/fork.png)

2. Select your Username as the destination for the fork.

3. Verify that the repository is under your username: `<GH_Username>/<repo_name>`

4. Click the green `code` button, then click the icon next to the SSH URL to copy the .git path.

   ![](./assets/ssh.png)

5. Open the terminal and `cd` into your mef folder: `cd ~/mef`.

6. Next, select the destination where you want to save the repository then type: `git clone <paste_git_url_here>`

   ![](./assets/git_clone.png)

7. `cd` into the new directory and you're ready to code. Happy coding!

   <br>

## To commit and push your work to GitHub

1. In the VM Terminal, `cd` into the folder you want to push up.
2. Add your files to a staging mode: `git add -A`
3. _(Optional)_ - You can run `git status` to observe your files
4. Commit your files to version control: `git commit -m "PUT A DESCRIPTION OF WHAT YOU'RE COMMITTING HERE"`
5. _(Optional)_ - You can run `git status` to observe what you committed
6. _(Optional)_ - You can run `git log` to see a history of all your commits.
7. Push to GitHub: `git push`. You can now goto your repo on GitHub to see your new files.

<!-- NOTE - if you get an error, try `git push origin main`. Your primary branch will be named `master` or `main`. -->

   <!-- You can now goto your repo on GitHub to see your new files. NOTE - if you do not see your updates, please select the dropdown menu on the top right (it'll probably say "Main") and select the "Master" branch. -->

<br>

## Submitting Your Work via Pull Request

1. In your repository, click on Pull Requests which is placed underneath the repo name.
   ![](./assets/pull_requests.png)
2. Click on the New pull request button.
   ![](./assets/new_pr.png)
3. Confirm that the base repository is the ModernEngineering org name and the head repository is your GH username. Once that's been verified, click on the Create pull request button.
   ![](./assets/create_pr1.png)
4. In the Title input, type in `MEF - <your_first_name> <your_last_name>` then click on Create pull request to officially submit your lab or homework.
   ![](./assets/create_pr2.png)

## To stop a running port

If you get a message that a port is in use, you can kill it with this command: `sudo kill -9 $(sudo lsof -t -i:3000)`

- Replace `3000` with the port number you want to stop.
- [Reference](https://tecadmin.net/kill-process-on-specific-port/)

## Viewing Slide Decks With Clickable URLS

When viewing a slide in the github repository if you > click on the download button.

![](./assets/download-icon.png)

You will then have the slide open in your browser window and any urls in the slide deck lesson will be clickable to direct you to further lesson resources / exercises.  In additional you can also navigate between slides by also typing in the slide page number to direct you in case you get lost at any time.

![](./assets//slide-screenshot-url.png)

## Fixing PostgreSQL Authentication Error

* Before proceeding make sure that you have spelled the password correct which should be **postgres**

To resolve a PostgreSQL authentication error by setting the authentication method to `md5`, run the following script:

1. `sudo sh ~/mef/start-here/fixpg.sh`

If this doesn't work, try the following:

1. **Open `pg_hba.conf` for Editing**:
   In the terminal, run:

   `sudo vi /var/lib/pgsql/data/pg_hba.conf`
   <br>

   This command opens the `pg_hba.conf` file in vi editor with superuser privileges.

2. **Enter Insert Mode**:
   - Press `i` to enter insert mode in vi, which allows you to make changes to the file.

   ![](./assets//postgres-before.png)

3. **Edit Authentication Method**:
   - Find the line corresponding to the `postgres` user, typically:
   ```
   local   all   postgres   peer
   ```
   ![](./assets/postgres-before.png)

- Change `peer` to `md5`:
  ```
  local   all   postgres   md5
  ```
  ![](./assets/postgres-md5.png)

4. **Save and Exit**:
   - Press `Esc` to exit insert mode and return to command mode.
   - Type `:wq` and then press `Enter` to save the changes and close the editor.

   ![](./assets/postgres-wq.png)

   <br>

5. **Restart PostgreSQL**:
Restart the PostgreSQL service to apply changes:

   - `sudo systemctl restart postgresql`

   ![](./assets/restart-postgresql.png)


Now, PostgreSQL will use `md5` authentication for the `postgres` user.

#### Configuring a Global git ignore

> IMPORTANT: **THIS STEP IS CRITICAL**

Everyone should have a global **git ignore** file so that you don’t have to worry about making the appropriate entries in a project’s git ignore.

First, create the file:  `touch ~/.gitignore_global`

Next, configure git to use this file:  `git config --global core.excludesfile ~/.gitignore_global`

Finally, lets put some good stuff in there by editing the newly created `.gitignore_global` file using VS Code:

1. `code ~/.gitignore_global` to open the file in VS Code

2. Copy/paste the following into `~/.gitignore_global`:

```sh
# This is a list of rules for ignoring files in every Git repositories on your computer.
# See https://help.github.com/articles/ignoring-files

# Compiled source #
###################
*.class
*.com
*.dll
*.exe
*.o
*.so
core.*

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log

# OS generated files #
######################
._*
.DS_Store
.DS_Store?
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# Testing #
###########
.rspec
capybara-*.html
coverage
pickle-email-*.html
rerun.txt
spec/reports
spec/tmp
test/tmp
test/version_tmp
/coverage

# node #
########
node_modules
/.pnp
.pnp.js
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# production
/build

# CTags #
#########
tags

# Env #
#######
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# Misc #
.eslintcache

```



## Additional Links
