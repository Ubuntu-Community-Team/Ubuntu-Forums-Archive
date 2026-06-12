---
title: "Access a &quot;hidden&quot; directory?"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by Worlds Tallest Engineer on 2011-08-22
I am getting this error.
```
[SIZE=1]./tidy.php: Permission denied [/SIZE]
 
```I want to use chmod to change the file-permissions on tidy.php.  But I don't know where it is? So I did this in the terminal.  
```
[SIZE=1]**sudo apt-file search tidy.php **[/SIZE]
 [SIZE=1]dotlrn:  [/SIZE] [SIZE=1][FONT=FreeMono, monospace]/usr/share/dotlrn/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean/tidy.php [/FONT][/SIZE]
 [SIZE=1]openacs:[/SIZE]  [SIZE=1][FONT=FreeMono, monospace]/usr/share/openacs/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean/tidy.php [/FONT][/SIZE]
 [SIZE=1]serendipity: [FONT=FreeMono, monospace]/usr/share/serendipity/www/htmlarea/plugins/SuperClean/tidy.php [/FONT][/SIZE]
  
```But I can not access these directories for some reason.  
```
[SIZE=1]user@computer:/usr/share$ cd /usr/share/openacs/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean [/SIZE]
 [SIZE=1]bash: cd: /usr/share/openacs/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean: No such file or directory [/SIZE]
  
 user@computer[SIZE=1]:/usr/share$ cd /usr/share/dotlrn/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean [/SIZE]
 [SIZE=1]bash: cd: /usr/share/dotlrn/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean: No such file or directory [/SIZE]
  
 [SIZE=1]user@computer:/usr/share$ cd /usr/share/serendipity/www/htmlarea/plugins/SuperClean [/SIZE]
 [SIZE=1]bash: cd: /usr/share/serendipity/www/htmlarea/plugins/SuperClean: No such file or directory [/SIZE]
 
```Douse anyone know how I can get into these files and change there permissions?

---

### Post by scorp123 on 2011-08-22
> **Worlds Tallest Engineer said:**
> I am getting this error.
```
[SIZE=1]./tidy.php: Permission denied [/SIZE]
 
```I want to use chmod to change the file-permissions on tidy.php.  But I don't know where it is? Your use of dot-slash "./" (which means "right here" in Unix lingo) suggests the file is right there in your home directory. Or where ever you were in that moment when you tried to execute the file. But that's irrelevant anyway. Someone correct me: But isn't PHP supposed to be interpreted by a web server because the language is embedded into HTML? [http://en.wikipedia.org/wiki/Php](http://en.wikipedia.org/wiki/Php)

Can you please explain more what exactly you are trying to achieve here?

---

### Post by fdrake on 2011-08-22
> 
sudo apt-file search tidy.php 
 dotlrn:   /usr/share/dotlrn/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean/tidy.php 
 openacs:  /usr/share/openacs/packages/acs-templating/www/resources/xinha-nightly/plugins/SuperClean/tidy.php 
 serendipity: /usr/share/serendipity/www/htmlarea/plugins/SuperClean/tidy.php 

those packages aren't installed yet that's why their urls don't exist yet
to serach for a file use
```

find /location/path -name filename

```
/location/path = /home/john/Desktop
filename= movie.avi
```
find ~/ -name tidy.php
```

---

### Post by Worlds Tallest Engineer on 2011-08-22
I'm trying to replace our old fedora server with a new Ubuntu box.  After the old server died all we have left is the package we put on sourceforge.net.   So I downloaded and untared  WSUQT, and tried to install it.  

```
 user@computer:/etc/php5/cli$ **cd ~/Desktop/wsuqt  **
 user@computer:~/Desktop/wsuqt$ **sudo ./install.sh  **
 WSUQ&T INSTALLATION  
 Specify the desired WSUQ&T file directory (ie. /var/www/html/hwol):[FONT=Courier New] **Stuff  **[/FONT]
 Enter your dns address (ie. http://fakeURL.wsu.edu): **Stuff**
 Enter the directory postgre is installed in (ie. /usr/local/pgsql):** Stuff**
 Enter the database name:** More Stuff  **
 Enter the database username: **Stuff**
  Please specify an administrator email address:** More stuff** 
 Specify the location of boost and pqxx libraries:  
 (Read INSTALL file if these libraries are not in the same location)  
  **Suff **
 Specify the location of the php interpreter: **Final stuff**

```(Note: bold text are things I typed)

However after I finish entering in all the data, wsuqt spit out a tone of lines into the terminal.  One of the error was at the very end of the text dump.   I copied that section of the code I pasted it below.  

```
       
 ./install.sh: 119: ./tidy.php: Permission denied  
 
```note: wsuqt = Washington State University quiz and tutorial system.

---

### Post by Worlds Tallest Engineer on 2011-08-22
> aren't installed yetThis might be a dumb question but... How did I find a non-installed file?  Will I need to download more stuff?

I tried using this, and got nothing.  
```
user@computer:~$ find ~/ -name tidy.php
user@computer:~$ locate tidy.php
user@computer:~$
```

---

### Post by fdrake on 2011-08-22
> **Worlds Tallest Engineer said:**
> I'm trying to replace our old fedora server with a new Ubuntu box.  After the old server died all we have left is the package we put on sourceforge.net.   So I downloaded and untared  WSUQT, and tried to install it.  

```
bryan@HonorsServer:/etc/php5/cli$ **cd ~/Desktop/wsuqt  **
 bryan@HonorsServer:~/Desktop/wsuqt$ **sudo ./install.sh  **
 WSUQ&T INSTALLATION  
 Specify the desired WSUQ&T file directory (ie. /var/www/html/hwol):[FONT=Courier New] **/var/www/html/hwol  **[/FONT]
 Enter your dns address (): 
**http://domain.com  **
 Enter the directory postgre is installed in (ie. /usr/local/pgsql):** /usr  **
 Enter the database name:** database  **
 Enter the database username: **john**
Please specify an administrator email address:** user@email.com ** 
 Specify the location of boost and pqxx libraries:  
 (Read INSTALL file if these libraries are not in the same location)  
 **/usr/lib  **
 Specify the location of the php interpreter: **/etc/php5/cli  **

```(Note: bold text are things I typed)

However after I finish entering in all the data, wsuqt spit out a tone of lines into the terminal.  One of the error was at the very end of the text dump.   I copied that section of the code I pasted it below.  

```
     cp grade.cgi /var/www/html/hwol/bin/grade.cgi  
 cp: cannot stat `grade.cgi': No such file or directory  
 make: *** [install] Error 1  
 Creating the database wsuqtdb171224  
 Restoring the schema  
 Restoring the data.  
  
 Ignore the error on BLOB COMMENTS.  Disable triggers  
  should not execute on it, but it does.  It is a glitch with pg_restore  
  
 ./install.sh: 119: ./tidy.php: Permission denied  
 
```

note: wsuqt = Washington State University quiz and tutorial system.

do you build-essential installed?

```
sudo apt-get install build-essential
```
than try to compile the source again. try to post the whole output since is very hard to understand what you are missing from only one piece of it.

---

### Post by whatthefunk on 2011-08-22
> **Worlds Tallest Engineer said:**
> This might be a dumb question but... How did I find a non-installed file?  Will I need to download more stuff?

I tried using this, and got nothing.  
```
bryan@HonorsServer:~$ find ~/ -name tidy.php
bryan@HonorsServer:~$ locate tidy.php
bryan@HonorsServer:~$
```

You were using apt-file search which searches for files in deb packages.  Maybe you have deb packages that arent yet installed?

---

### Post by fdrake on 2011-08-22
> **Worlds Tallest Engineer said:**
> This might be a dumb question but... How did I find a non-installed file?  Will I need to download more stuff?

I tried using this, and got nothing.  
```
bryan@HonorsServer:~$ find ~/ -name tidy.php
bryan@HonorsServer:~$ locate tidy.php
bryan@HonorsServer:~$
```

that command isn't searching for files in your hdd is looking for filenames that belongs to packages in the repositories.  it basically does an online query.

you can try to search the whole disk with

> sudo find / -name tidy.php

---

### Post by Worlds Tallest Engineer on 2011-08-22
> sudo find / -name tidy.php
Well that one made my computer chug for a while, but still found nothing.

---

### Post by Minimal ™ on 2011-08-22
> **Worlds Tallest Engineer said:**
> Well that one made my computer chug for a while, but still found nothing.

If it didn't find anything, the given file does not exists on your system.

---

