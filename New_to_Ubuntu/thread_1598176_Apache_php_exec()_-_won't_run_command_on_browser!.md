---
title: "Apache php exec() - won't run command on browser!"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by kauboy on 2010-10-16
Hi folks,

I don't know where to post this, please point me in the right direction if I'm wrong in posting this here.

I have a command line utility called isql (which I use to connect to a remote MS :( SQL 2005 server using iODBC and FreeTDS) for issuing SQL queries. I wanted to create a GUI for it and so decided to take the apache+php route to create a web interface. Here is the problem.

I have a php file which has the lines system("isql --version") and system("man isql"). These two lines print out proper data both when executed via the Terminal as well as from the browser ([http://localhost/file.php](http://localhost/file.php)) Tried redirecting their output to a text file by appending "> textfile" at the end of those system calls, and they both print properly from Terminal as well as browser.

BUT, when I do system("isql") or system("isql ODBCdsn username 'password'") which is the useful command, it WORKS via the Terminal but DOES NOT PRINT OUT ANYTHING on the browser. Same result on printing to a file - when executed via Terminal, it writes output to the file but when done through browser, it just creates an empty file.

I have been breaking my head over this for a while now and Googling did not help much either. It looks like the isql command is visible to the browser as it prints out the version number but it won't execute the "isql ODBCdsn username 'password'" command. Do I need to modify access permissions for apache or run it as privileged user?

Thanks for any help!

PS: Using shell_exec() or exec() in place of system() give the same results.

---

### Post by kauboy on 2010-10-16
Update: Tried changing User and Group in apache2.conf file to my default admin user, restarted apache, system("whoami") returned my admin user on browser, but it changed nothing. I still get only blank output on system("isql ODBC username 'password'") or even for system("mysql") for that matter. Using absolute path /usr/bin/isql or /path/to/mysql made no difference. Anybody?? :(

---

### Post by kauboy on 2010-10-16
SOLVED! For whatever reason, redirecting STDERR to STDOUT by appending 2>&1 at the end of the command - like system("isql ODBCdsn username 'password' 2>&1") - showed up the output on the browser. To print to a file instead, use system("isql ODBCdsn username 'password' 2>/path/to/file")

I found it strange but it works! :)

---

