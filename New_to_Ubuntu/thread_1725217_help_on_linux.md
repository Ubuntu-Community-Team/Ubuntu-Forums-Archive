---
title: "help on linux"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by sandy0594 on 2011-04-09
Hey all,i am very new to linux and of course to this community..I really appreciate if someone let me know which version or distribution of   linux is better if one is into programming.I am in the learning stage of programming languages...I need Java,Oracle and all these things to be supported.So,which is the best one which suits my purpose

---

### Post by ivanovnegro on 2011-04-09
You are in the Ubuntu Forums, so it would be logically to try Ubuntu (Gnome/KDE) or whatever Linux distribution in general.
I would recommend you to download Ubuntu 10.10 or 10.04 (LTS) maybe with Gnome and burn it onto a CD and give it a test.
You can of course use your programming skills on Ubuntu.

Btw, welcome! :)

---

### Post by sandy0594 on 2011-04-09
Thanks for ur posts..But,i learned from some of the oracle forums that Oracle version 10 is not supported in ubuntu..that's what made me to post the question may be u people would provide a better **suggestion**..
I installed Ubuntu 10.10 a day back through windows installer **wubi**

---

### Post by ivanovnegro on 2011-04-09
I admit Im not sure about Oracle as Im not a programmer maybe someone else will have a better suggestion.
Btw, Wubi installs are always somehow problematical, they dont behave like original Ubuntu installs. In the future I recommend you anyway to install Ubuntu again to have a better experience. You can google about why its not recommended to install Ubuntu via Wubi, its a great idea to but for me only to test Ubuntu.

---

### Post by Robing Goodfellow on 2011-04-09
Sandy, the answer to your question is "whichever you want."  The distro and version of Linux that you use isn't what makes or breaks your programming experience, its the software you install.  In my case, I use Ubuntu 10.10 for my OS.  For my programming (mostly C++, with some Php and Java script) I use Netbeans, which is available in the Software Center.

regards, Richard

---

### Post by sandy0594 on 2011-04-09
The problem is with the database,i am a reular at oracle forums.One of the Oracle Ace Director mentioned that oracle v 10 is not supported for ubuntu distributions..

---

### Post by Robing Goodfellow on 2011-04-09
Have you tried this?

[http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0](http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0)

Also, there appear to be many debian packages for Oracle 10.  In Ubuntu, download the debian package, double click and it should install itself, with prompts as required.

HTH, Richard

---

### Post by sandy0594 on 2011-04-09
> 


10gR2 is out of Premier Support and Ubuntu is not a supported/certified OS

[http://download.oracle.com/docs/cd/B19306_01/install.102/b15660/toc.htm](http://download.oracle.com/docs/cd/B19306_01/install.102/b15660/toc.htm)




This is bothering me...It's from a highly rated member of oracle community

---

### Post by Robing Goodfellow on 2011-04-09
Perhaps certified and supported should not have been used concurrently?  It would appear that there IS a method for running your Oracle in Ubuntu 10.10, ergo it's level of support and certification is immaterial, unless I am misunderstanding something.  Not being snarky, just don't understand the dilemma.  Could be the respected member of the Oracle community is just wrong, or just didn't know?  I dunno.  Try it.  See what happens.

regards, Richard

---

### Post by Karlchen on 2011-04-09
Hello, sandy0594.
> This is bothering me...It's from a highly rated member of oracle communityWell, of course, Oracle may wish you to use Redhat which is a supported Linux version. ;)

Yet, there are hints that Oracle can be persuaded to run on Ubuntu as well, even though Oracle only bothers to provide .RPM installation packages whereas Ubuntu needs .DEB installation packages:

+ [**Installing Oracle 11gR2 on Ubuntu 9.10**]("http://mikesmithers.wordpress.com/2010/03/14/installing-oracle-11gr2-on-ubuntu-9-10/")
+ **[Oracle 10g Express on Ubuntu 10.10 AMD 64-bit howto]("http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0")**

In case _official_ support for Oracle installations is an essential requirement then Redhat or CentOS may be the primary choice.

Kind regards,
Karl

---

### Post by sandy0594 on 2011-04-09
I finally decided to give it a try..I am downloading 10gR2 for Linux..The installation steps are a bit confusing for a beginner like me..In windows it's just clicking **next  **and so forth.Can anyone explain how to carry out this installation in Linux

```
Points to be noted:
1)Oracle requires at least 3-4 GB of free space

2)I have two OS running in my pc..Windows Xp and Ubuntu 10.10  

3)My hardware configuration:Intel E7500 core 2 duo processor,500 GB Hard Drive,4 GB of RAM
```

---

### Post by Robing Goodfellow on 2011-04-09
If you are installing via the instructions on the link I posted earlier ([ http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0]("http://http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0") ) then it seems to me that the instructions are pretty step by step.

I'm wondering if your confusion is due to lack of familiarity with command line / terminal use.  If so, once your download is done, open the terminal (Applications>Accessories>terminal)

then enter commands as directed.  For example, in step 5.

```

$ cd Downloads
$ sudo apt-get install libc6-i386
$ wget [http://oss.oracle.com/debian/dists/unstable/main/binary-i386/libaio_0.3.104-1_i386.deb](http://oss.oracle.com/debian/dists/unstable/main/binary-i386/libaio_0.3.104-1_i386.deb)
$ sudo dpkg -i --force-architecture libaio_0.3.104-1_i386.deb
$ sudo dpkg -i --force-architecture oracle-xe*

```the $ sign is just the prompt you will see in the terminal.  You type "cd Downloads" without the quote marks, then hit enter.  This changes your working directory to Downloads, which, by default, is where your Oracle download went.  You will immediately get a new line with a new prompt.  that's the terminal telling you it's done and waiting.  Now type the next line "sudo apt-get install libc6-i386"

Terminal will ask you for your password.  Type in the password you set as administrator when you installed.  The command is using apt-get, a standard command, to install the file libc6-i386.  

Just continue on with the instructions as shown on the above link and you should have no problem.  If you do, come back and let us know and we'll get it figured out.

regards, Richard

---

### Post by sandy0594 on 2011-04-10
Hey Richard,i tried as per ur advice..But,i am getting some errors

```
sandy@ubuntu:~$ cd Downloads
sandy@ubuntu:~/Downloads$  sudo apt-get install libc6-i386
[sudo] password for sandy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libc6-i386' has no installation candidate
sandy@ubuntu:~/Downloads$ wget http://oss.oracle.com/debian/dists/u...104-1_i386.deb
--2011-04-10 10:22:44--  http://oss.oracle.com/debian/dists/u...104-1_i386.deb
Resolving oss.oracle.com... 141.146.12.120
Connecting to oss.oracle.com|141.146.12.120|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-04-10 10:22:45 ERROR 404: Not Found
```.

My download file name is "**10201_database_linux32.zip**"..Can you explain me how to carry out the installation of the above file

---

### Post by sandy0594 on 2011-04-10
Hey all, I am very new to Linux..I have downloaded Oracle database for Linux.But,unfortunately i am unable it to install on Linux
BTW,I am running Ubuntu 10.10...The downloaded file is **10201_database_linux32.zip**.How to install a file with .zip extension.Could someone kindly suggest me how to carry out the installation

---

### Post by uRock on 2011-04-10
Unzip it by right-clicking and selecting to "**extract here**" then read the **read me** file in the extracted directory.

---

### Post by sandy0594 on 2011-04-10
As far as i have seen,there is no read me file

```
sandy@ubuntu:~/Downloads/Oracle/database$ dir
doc  install  response    runInstaller  stage  welcome.html
```

---

### Post by rosencrantz on 2011-04-10
My guess would be
sh runInstaller
or 
sudo sh runInstaller

Welcome.html might have further instructions.
Oh, and your shell commands are still Windows-based (dir instead of ls), which might get you into trouble at some point. Here's a cheat sheet
[http://www.rain.org/~mkummel/unix.html](http://www.rain.org/~mkummel/unix.html)

---

### Post by sandy0594 on 2011-04-10
I am sad by seeing this

```
sandy@ubuntu:~/Downloads/Oracle/database$ sh runInstaller
Starting Oracle Universal Installer...

Checking installer requirements...

Checking operating system version: must be redhat-3, SuSE-9, redhat-4, UnitedLinux-1.0, asianux-1 or asianux-2
                                      Failed <<<<

Exiting Oracle Universal Installer, log for this session can be found at /tmp/OraInstall2011-04-10_11-30-42AM/installActions2011-04-10_11-30-42AM.log
```

I am kinda liking ubuntu..now,this says i can't run oracle in this..what's this ***?

---

### Post by rosencrantz on 2011-04-10
Well, it is probably easier to install a version that is aware of Ubuntu ;-) The installer messages mention Suse 9, so this could be *really* old (Ubuntu has been around only since 2004).
You can try the more recent instructions from the Ubuntu wiki
[https://help.ubuntu.com/community/Oracle](https://help.ubuntu.com/community/Oracle)
Oracle's repository doesn't seem to be extremely up to date either, so you can also try downloading one of the .deb's here [http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html](http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html)
and install it with sudo dpkg -i <packagename>.deb
Seems to be the most recent stable version.

Cheers,rosencrantz

---

### Post by sandy0594 on 2011-04-10
I think Oracle doesn't give support for Ubuntu distribution.The most recent version of oracle doesn't offer support [http://download.oracle.com/docs/cd/E11882_01/install.112/e16763/pre_install.htm#BABFDGHJ](http://download.oracle.com/docs/cd/E11882_01/install.112/e16763/pre_install.htm#BABFDGHJ)

Too sad

However,i am downloading this: [http://www.oracle.com/technetwork/da...ft-102048.html](http://www.oracle.com/technetwork/da...ft-102048.html)
Let's checkout what happens
:(

---

### Post by alphacrucis2 on 2011-04-10
There is an Oracle wiki talking about installing on Debian and Ubuntu so it appears that it ought to be possible:

[http://wiki.oracle.com/page/Installing+Oracle+on+Debian+%2F+Kubuntu+%2F+Ubuntu]("http://wiki.oracle.com/page/Installing+Oracle+on+Debian+%2F+Kubuntu+%2F+Ubuntu")

It's fairly old though.

---

### Post by yeats on 2011-04-10
Unless you have a particular need for Oracle (assuming you do), you might want to check out PostgreSQL ([http://www.postgresql.org/](http://www.postgresql.org/)), which has a lot of features that compare to Oracle's capabilities (from what I understand... I have not used Oracle).  I would imagine a recent version of Postgres would probably have more features - and you definitely can't beat the price.

To install: 

```
sudo apt-get install postgresql
```

---

### Post by sandy0594 on 2011-04-10
SQL and PL/SQL is what i work..

---

### Post by SeijiSensei on 2011-04-10
Why don't you use VirtualBox to create virtual machine and install CentOS into it?  Then install Oracle into that.

---

### Post by yeats on 2011-04-10
> **sandy0594 said:**
> SQL and PL/SQL is what i work..

From PostgreSQL's [About page]("http://www.postgresql.org/about/"):

"PostgreSQL runs stored procedures in more than a dozen programming languages, including Java, Perl, Python, Ruby, Tcl, C/C++, and its own PL/pgSQL, which is similar to Oracle's PL/SQL. Included with its standard function library are hundreds of built-in functions that range from basic math and string operations to cryptography and Oracle compatibility."

Don't know if that helps, but if you can't get Oracle to install and are considering a free replacement, this might work.

---

### Post by sandy0594 on 2011-04-10
Hey,i installed Oracle 10g Xe by following [http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0](http://forums.oracle.com/forums/thread.jspa?threadID=2200434&tstart=0)

The installation went well with some problems in b/w..if someone can sort these errors it would be of great help

```


sandy@ubuntu:~/Downloads$ sudo apt-get install libc6-i386
[sudo] password for sandy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libc6-i386' has no installation candidate
sandy@ubuntu:~/Downloads$ wget http://oss.oracle.com/debian/dists/unstable/main/binary-i386/libaio_0.3.104-1_i386.deb
--2011-04-11 00:06:16--  http://oss.oracle.com/debian/dists/unstable/main/binary-i386/libaio_0.3.104-1_i386.deb
Resolving oss.oracle.com... 141.146.12.120
Connecting to oss.oracle.com|141.146.12.120|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6018 (5.9K) [text/plain]
Saving to: `libaio_0.3.104-1_i386.deb'

100%[======================================>] 6,018       21.6K/s   in 0.3s    

2011-04-11 00:06:17 (21.6 KB/s) - `libaio_0.3.104-1_i386.deb' saved [6018/6018]

sandy@ubuntu:~/Downloads$ sudo dpkg -i --force-architecture libaio_0.3.104-1_i386.deb
Selecting previously deselected package libaio.
(Reading database ... 155192 files and directories currently installed.)
Unpacking libaio (from libaio_0.3.104-1_i386.deb) ...
Setting up libaio (0.3.104-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sandy@ubuntu:~/Downloads$ sudo dpkg -i --force-architecture oracle-xe*
Selecting previously deselected package oracle-xe-universal.
(Reading database ... 155201 files and directories currently installed.)
Unpacking oracle-xe-universal (from oracle-xe-universal_10.2.0.1-1.0_i386.deb) ...
This system does not meet the minimum requirements for swap space.  Based on 
the amount of physical memory available on the system, Oracle Database 10g 
Express Edition requires 1024 MB of swap space. This system has 254 MB 
of swap space.  Configure more swap space on the system and retry the installation.
Setting up oracle-xe-universal (10.2.0.1-1.0) ...
update-rc.d: warning: /etc/init.d/oracle-xe missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Executing Post-install steps...
-e You must run '/etc/init.d/oracle-xe configure' as the root user to configure the database.

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
sandy@ubuntu:~/Downloads$ sudo gedit 
sandy@ubuntu:~/Downloads$ nls_lang.sh
nls_lang.sh: command not found
sandy@ubuntu:~/Downloads$ sudo gedit nls_lang.sh
sandy@ubuntu:~/Downloads$ sudo /etc/init.d/oracle-xe configure

Oracle Database 10g Express Edition Configuration
-------------------------------------------------
This will configure on-boot properties of Oracle Database 10g Express 
Edition.  The following questions will determine whether the database should 
be starting upon system boot, the ports it will use, and the passwords that 
will be used for database accounts.  Press <Enter> to accept the defaults. 
Ctrl-C will abort.

Specify the HTTP port that will be used for Oracle Application Express [8080]:8080   

Specify a port that will be used for the database listener [1521]:1521

Specify a password to be used for database accounts.  Note that the same
password will be used for SYS and SYSTEM.  Oracle recommends the use of 
different passwords for each database account.  This can be done after 
initial configuration:
Confirm the password:

Do you want Oracle Database 10g Express Edition to be started on boot (y/n) [y]:y

Starting Oracle Net Listener...Done
Configuring Database...Done
Starting Oracle Database 10g Express Edition Instance...Done
Installation Completed Successfully.
To access the Database Home Page go to "http://127.0.0.1:80/apex"
sandy@ubuntu:~/Downloads$ su - oracle
Password: 
oracle@ubuntu:~$ echo "source /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh" >> $HOME/.bashrc
oracle@ubuntu:~$ exit
logout
sandy@ubuntu:~/Downloads$ su - oracle
Password: 
oracle@ubuntu:~$ printenv
SHELL=/bin/bash
TERM=xterm
XDG_SESSION_COOKIE=bf05847f2afbf1357be2e2c500000006-1302461321.562245-1524030657
USER=oracle
MAIL=/var/mail/oracle
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
PWD=/usr/lib/oracle/xe
LANG=en_US.UTF-8
SHLVL=1
HOME=/usr/lib/oracle/xe
LOGNAME=oracle
DISPLAY=:0.0
XAUTHORITY=/var/run/gdm/auth-for-sandy-K7PCMj/database
COLORTERM=gnome-terminal
_=/usr/bin/printenv
oracle@ubuntu:~$ su -oracle
su: invalid option -- 'o'
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and
                                keep the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

oracle@ubuntu:~$ sqlplus / as sysdba
sqlplus: command not found




```

---

### Post by SeijiSensei on 2011-04-10
> This system does not meet the minimum requirements for swap space.  Based on the amount of physical memory available on the system, Oracle Database 10g Express Edition requires 1024 MB of swap space. This system has 254 MB of swap space.  Configure more swap space on the system and retry the installation.


This message means exactly what it say.  Oracle wants a minimum swap space of 1024 MB.  The simplest way to solve this is to create a swapfile of at least 768 MB and configure it as a secondary swap device in /etc/fstab.  This method avoids have to repartition the hard drive.  There are lots of tutorials online about adding swap.  The first result of searching for "linux add swap" gave this this: [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/).

@Karichen
I used the "Report abuse" button to ask the moderators to merge these two threads.  It's unfortunate that it says "Report abuse".  Pressing the Report button in a vBulletin forum like this one sends a note directly to the moderators.  It makes it more likely that someone will see your message about the duplication between these threads.  Thanks for caring!

---

### Post by sandy0594 on 2011-04-11
I could login to sqlplus with minor glitches,if anone could say me the cause of these problems,it will be better

```


/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found

SQL*Plus: Release 10.2.0.1.0 - Production on Mon Apr 11 17:33:42 2011

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

SQL> conn scott
Enter password: 
Connected.



```

I am attaching screen shots,one is in the terminal and the other one is sqlplus prompt

---

### Post by sandy0594 on 2011-04-13
I installed oracle 10g R2 in Ubuntu 10.10...Finished the installation successfully,i could even get into **isqlplus.**.But,i couldn't  run on ** sqlplus**

```

oracle@ubuntu:~$ sqlplus / no log
sqlplus: command not found

```

---

### Post by sandy0594 on 2011-04-13
The reason i got the above error is that i didn't set up the environment variables which caused terminal to bless me with errors
Anyhow,to sort those errors we need to add the below in **.bash_profile** so that it will take environment variables automatically whenever we login to that particular user

> 

export ORACLE_SID=<yourSid>
export ORACLE_HOME=/opt/oracle/oracle/product/10.2.0/db_2
export PATH=$PATH:/opt/oracle/oracle/product/10.2.0/db_2/bin

After adding the above,run the **.bash_profile** 
> 
**..bash_profile**


Now,we won't get sqlplus:command not found error by doing the above
But,in order to work with sqlplus we need to do lil home work as below:

> 

oracle@ubuntu:~$ sqlplus / as sysdba

SQL*Plus: Release 10.2.0.1.0 - Production on Thu Apr 14 01:06:12 2011

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Connected to an idle instance.

SQL> startup
ORACLE instance started.

Total System Global Area 1040187392 bytes
Fixed Size            1223296 bytes
Variable Size          272631168 bytes
Database Buffers      759169024 bytes
Redo Buffers            7163904 bytes
Database mounted.
Database opened.

SQL> conn scott
Enter password: 
Connected.


Note:We need to login to the user where we installed Oracle..

Thanks for all your replies and suggestions..

---

