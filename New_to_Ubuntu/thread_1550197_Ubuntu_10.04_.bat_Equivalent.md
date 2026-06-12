---
title: "Ubuntu 10.04 .bat Equivalent?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by DaGeek247 on 2010-08-10
I have Googled this, and the answers on the other posts were not satisfactory. I am trying to set up Xampp, like I had WAMP. (Don't use it, it was the start to all of [these problems]("http://forums.fedoraforum.org/showthread.php?t=249741"), PM Me if you want to know about it.) All I have to do is click Applications>Xampp>Start Xampp to get it up and running, just like the way WAMP is set up. I have created all the menus, and files to run the required code.

How would i set up a file to Start the Xampp services with this code:
```

/opt/lampp/lampp start

``` just by clicking on a menu item in the Applications menu? The only reason i mentioned .bat is because that is what runs code in windows. (which, btw, if you went to the link above, it did not install, and it costs money to contact Microsoft, So I am just setting my computer up as an Ubuntu only system) Any help would be appreciated. 

(For those who read my post about the Ubuntu screen error, (It dissapeared, so i cant give a link) I did fix the screen error by installing all the suggested files in the reinstall of ubuntu, thanks for the suggestions.)

---

### Post by oldfred on 2010-08-10
bash files are the nearest things to .bat files in windows.

But can you not right click on applications, edit menus, new item and add it as a menu item?

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
Whiptail is a program that allows shell scripts to display dialog boxes
[http://en.wikibooks.org/wiki/Bash_Shell_Scripting#Using_whiptail](http://en.wikibooks.org/wiki/Bash_Shell_Scripting#Using_whiptail)

---

### Post by sandyd on 2010-08-10
> **DaGeek247 said:**
> I have Googled this, and the answers on the other posts were not satisfactory. I am trying to set up Xampp, like I had WAMP. (Don't use it, it was the start to all of [these problems]("http://forums.fedoraforum.org/showthread.php?t=249741"), PM Me if you want to know about it.) All I have to do is click Applications>Xampp>Start Xampp to get it up and running, just like the way WAMP is set up. I have created all the menus, and files to run the required code.

How would i set up a file to Start the Xampp services with this code:
```

/opt/lampp/lampp start

``` just by clicking on a menu item in the Applications menu? The only reason i mentioned .bat is because that is what runs code in windows. (which, btw, if you went to the link above, it did not install, and it costs money to contact Microsoft, So I am just setting my computer up as an Ubuntu only system) Any help would be appreciated. 

(For those who read my post about the Ubuntu screen error, (It dissapeared, so i cant give a link) I did fix the screen error by installing all the suggested files in the reinstall of ubuntu, thanks for the suggestions.)
```

sudo ln /opt/lampp/lampp /usr/bin/lampp
sudo nano /usr/bin/startlampp

```
This will create a link between the lampp executables, and create a new file called startlampp

we want to run lampp with the commands "/opt/lampp/lampp start", so we enter it into the file
```

/opt/lampp/lampp start

```save
then run 
```

sudo chmod 667 /usr/bin/startlampp
```
to make the file executable

now just run


```

sudo startlampp
``` to start LAMPP

Just for convineance, the instructions also linked /opt/lampp/lampp to /usr/bin/lampp.
so for any commands you want to run with lampp, ex: /opt/lamp/lampp start, you can also just simply run lampp start.

---

### Post by DaGeek247 on 2010-08-10
I mentioned that the problem did not lie in the creation of the menus. I also do not have any problems with the coding. I am having a problem running my code from the menu. It just doesn't run, and I can't see what the error is to try to fix it.

I now have two questions:
how do i put in a "pause" command to wait for the user to press a key before it exits?
And how do i set up a menu item to run some code?

@carlee
could you explain what is happening in more detail? I am still new to Ubuntu.

---

### Post by sandyd on 2010-08-10
> **DaGeek247 said:**
> I mentioned that the problem did not lie in the creation of the menus. I also do not have any problems with the coding. I am having a problem running my code from the menu. It just doesn't run, and I can't see what the error is to try to fix it.

I now have two questions:
how do i put in a "pause" command to wait for the user to press a key before it exits?
And how do i set up a menu item to run some code?
ah. heres the problem.
lampp must be started with sudo, because it hooks up sockets (port 80). However, sudo is text-based,
so in order for it to work, you need to add
```

gksudo
``` (gnome)

or ```

kdesudo
```(kde) in front of the command to make it run.

Its the equivilent of sudo, except in a graphical format.

---

### Post by oldfred on 2010-08-10
Anytime I have trouble with a menu item I copy it into a terminal and run it. Then you can see the errors in the terminal.

---

### Post by DaGeek247 on 2010-08-10
[IMG]http://ubuntuforums.org/root/Desktop/Screenshot.png[/IMG]
@oldfred
But that is just it! The code runs fine in the Ubuntu terminal! No problems at all!!!
basic code i want to run that works in terminal:
```

root@dageek247-desktop:~# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
root@dageek247-desktop:~# /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.7.3a...
XAMPP: Stopping Apache with SSL...
XAMPP: Stopping MySQL...
XAMPP: Stopping ProFTPD...
XAMPP stopped.

```i want to run that code from the menu. how do i?

@carlee
you are still not making since, but it seems like you are onto something. Can you explain?

---

### Post by louieb on 2010-08-10
[HOWTO  (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

Old How To - but its still active - it what I used when i ran Xampp - but don't think XAMPP has changed much.  and It does show how to set up an Xampp control pannel.

[IMG]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/IMG]

---

### Post by DaGeek247 on 2010-08-10
Thanks [louieb]("http://ubuntuforums.org/member.php?u=120176"), but I am thinking it would be cool to use Xampp from a menu like so:
[IMG]http://i36.tinypic.com/90yv6w.jpg[/IMG]

---

### Post by sandyd on 2010-08-10
> **DaGeek247 said:**
> [IMG]http://ubuntuforums.org/root/Desktop/Screenshot.png[/IMG]
@oldfred
But that is just it! The code runs fine in the Ubuntu terminal! No problems at all!!!
basic code i want to run that works in terminal:
```

root@dageek247-desktop:~# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
root@dageek247-desktop:~# /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.7.3a...
XAMPP: Stopping Apache with SSL...
XAMPP: Stopping MySQL...
XAMPP: Stopping ProFTPD...
XAMPP stopped.

```i want to run that code from the menu. how do i?

@carlee
you are still not making since, but it seems like you are onto something. Can you explain?
*sigh* just create a new text file called
LAMPP.desktop
and copy and paste this in
```

[Desktop Entry]
Comment=
Exec=gksudo /opt/lampp/lampp start
Name=LAMPP Start
NoDisplay=false
StartupNotify=true
Terminal=1
TerminalOptions=
Type=Application

```This will open LAMPP through a terminal.
Not sure if it works in gnome

---

### Post by DaGeek247 on 2010-08-10
@carlee
it worked!!!! Does the code have the ability to run more than one line of code?

---

### Post by sandyd on 2010-08-10
> **DaGeek247 said:**
> @carlee
it worked!!!! Does the code have the ability to run more than one line of code?
```

[Desktop Entry]
Comment=
Exec=gksudo /opt/lampp/lampp start && [extra command] && [extra command]
Name=LAMPP Start
NoDisplay=false
StartupNotify=true
Terminal=1
TerminalOptions=
Type=Application

```Note that gksudo will ONLY be used for /opt/lampp/lampp, so if you need sudo for the other commands as well, you will have to add it in for each one.
Ive also added a safeguard here. If the command before the && fails, the next command will not be run. If you want to disable this, change "&&" to "&"

---

### Post by louieb on 2010-08-10
one way to run multiple lines of code is to create s shell script - make it executable - and set your menu entry to the script.

another way is to separate the commands on the same line is to use a semicolon ;

---

