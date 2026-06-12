---
title: "What is next after installation??"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Alvyn on 2010-07-15
Hi 
 
Anyone can advise me why there isn't any GUI after I installed Ubuntu Server 10.04LTS?
 
I am presented with only CLI. 
 
What to do next?
 
Thanks.

---

### Post by firbolg on 2010-07-15
The server installation does not have a GUI.

---

### Post by Thelasko on 2010-07-15
Ubuntu server only has a command line interface.  If you need a gui, run:```
sudo apt-get install ubuntu-desktop
```

---

### Post by tarps87 on 2010-07-15
The server does not have a GUI, if you have a GUI you are likely to use it as a normal system which creates potential security issues.  Also the common way to connect to a server is using ssh as most servers are headless.

---

### Post by Alvyn on 2010-07-15
Hi Thelasko
 
Thanks for the command. However I got an error "app-get" command not found.
 
Very sorry as I am from MS background and totally new to Linux.
 
Regards
 
Alvyn
 
> **Thelasko said:**
> Ubuntu server only has a command line interface. If you need a gui, run:```
sudo apt-get install ubuntu-desktop
```

---

### Post by MCVenom on 2010-07-15
> **Alvyn said:**
> Hi Thelasko
 
Thanks for the command. However I got an error "app-get" command not found.
 
Very sorry as I am from MS background and totally new to Linux.
 
Regards
 
Alvyn
Well, just to make sure, are you working with a server here or a desktop? If it's a server, I don't recommend a gui. If it's a desktop, you should just reinstall with Ubuntu Desktop Edition.

Also, you mispelled it. It's 'apt-get', not 'app-get'. :P

---

### Post by tarps87 on 2010-07-15
Try typing the command again, I'm willing to be you typed app-get not apt-get :)

Edit: Beaten to it

---

### Post by Alvyn on 2010-07-15
Hi Tarps87
 
In this case, am I right to say that should I need to install third party programs such as Squirrelmail(Webmail for Linux), I have to configure it in CLI?
 
Does all Linux programs comes with CLI & GUI configuration?
 
Thanks
 
Alvyn
 
 
> **tarps87 said:**
> The server does not have a GUI, if you have a GUI you are likely to use it as a normal system which creates potential security issues. Also the common way to connect to a server is using ssh as most servers are headless.

---

### Post by Alvyn on 2010-07-15
Sorry, my mistake.
 
Type in "sudo apt-get install ubuntu-desktop"
 
Return Error : E:\Couldn't find package unbuntu-desktop
 
Must I download this package from any web site or it is already included in the 10.04LTS package?
 
Thanks.
 
> **tarps87 said:**
> Try typing the command again, I'm willing to be you typed app-get not apt-get :)
 
Edit: Beaten to it

---

### Post by Thelasko on 2010-07-15
> **Alvyn said:**
> Hi Thelasko
 
Thanks for the command. However I got an error "app-get" command not found.
 
Very sorry as I am from MS background and totally new to Linux.
 
Regards
 
Alvyn

Yeah, it's apt-get.  Not app-get.

Also, if you are intending on using this machine as a server, don't be afraid of the command line.  It's much easier than the Windows command line.

A quick summary:
"sudo" raises your privileges, so you can make system changes
"apt" is a program for installing software, it can download and install software securely with a few simple commands.

To install software:
```
sudo apt-get install *nameofprogram*
```
To remove software:
```
sudo apt-get remove *nameofprogram*
```

---

### Post by gr4nf on 2010-07-15
Not all linux programs do, but effectively all that you would use on a server do. To look at a larger list of software available from the command line but in a more graphical way, use the command:
```

aptitude

```
which is a front end to apt-get.

---

### Post by Thelasko on 2010-07-15
> **Alvyn said:**
> Sorry, my mistake.
 
Type in "sudo apt-get install ubuntu-desktop"
 
Return Error : E:\Couldn't find package unbuntu-desktop
 
Must I download this package from any web site or it is already included in the 10.04LTS package?
 
Thanks.

Your machine is set to look for software on the CD you installed Ubuntu from.  To enable more repositories [follow this guide.]("https://help.ubuntu.com/community/Repositories/CommandLine")

P.S. Summary:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list
```
put # in front of the CD section and remove the # from the Universe and Multiverse sections.  Save and then run:
```
sudo apt-get update
```

---

### Post by Alvyn on 2010-07-15
Hi All experts.
 
A million thanks for all the advises and patience.
Bear with me. I really need to overcome this "hurdle" to get into Linux. MS is too commercialize to be a solution.
 
Can anyone advise where to get information on CLI command and its usage with explanation for "real beginners" like myself.
 
Because humans tends to forget. 
I may configure something in CLI, however I may forget in the next 6 months or so. Is there a way to trace the configuration/settings in CLI?
I prefer GUI because it allows me to refer back to certain configuration/settings. Correct me if I am wrong.
 
Regards
 
Alvyn
 
> **Thelasko said:**
> Yeah, it's apt-get. Not app-get.
 
Also, if you are intending on using this machine as a server, don't be afraid of the command line. It's much easier than the Windows command line.
 
A quick summary:
"sudo" raises your privileges, so you can make system changes
"apt" is a program for installing software, it can download and install software securely with a few simple commands.
 
To install software:
```
sudo apt-get install *nameofprogram*
```
To remove software:
```
sudo apt-get remove *nameofprogram*
```

---

### Post by gr4nf on 2010-07-15
This:

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

is a great guide. Beyond that, use the command:
```

man "name of command"

```
to open a manual page for that command. Use the arrows to navigate and "q" to quit.

Good Luck!

---

### Post by Alvyn on 2010-07-15
Hi Gr4nf
 
Thanks.
 
:)
 
Alvyn
> **gr4nf said:**
> This:
 
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)
 
is a great guide. Beyond that, use the command:
```

man "name of command"

```
to open a manual page for that command. Use the arrows to navigate and "q" to quit.
 
Good Luck!

---

### Post by tarps87 on 2010-07-16
> **Alvyn said:**
> Sorry, my mistake.
 
Type in "sudo apt-get install ubuntu-desktop"
 
Return Error : E:\Couldn't find package unbuntu-desktop
 
Must I download this package from any web site or it is already included in the 10.04LTS package?
 
Thanks.

You done it again :)
Return Error : E:\Couldn't find package u**n**buntu-desktop
Try retyping it. As a hint you can use tab auto-complete, start typing a word such as apt then hit tab twice, you'll get a list, apt-g tab twice you'll get apt-get. Give it a try with the package name as well.

Oh an if you get board try installing moo ;)
apt-get moo

---

### Post by digitalcitizenx on 2010-07-16
Maybe the best thing for you to do, especially since you came from the windows world and can't do anything without a GUI, is to simply install the regular desktop version of Ubuntu THEN install LAMP (the server stuff) to let you play around with stuff until you "get it".

Great site for learning the command line:

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

also read this article:

[http://www.freesoftwaremagazine.com/articles/command_line_intro](http://www.freesoftwaremagazine.com/articles/command_line_intro)

Here is how to install LAMP in a regular Ubuntu desktop install:

[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

This is the recommended way to accomplish this task.

For further help regarding Ubuntu related topics see the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Lucid").

Good luck.

---

### Post by digitalcitizenx on 2010-07-16
A few more tips.

When you get the desktop installed, CTRL + ALT + F1 through F6 are separate terminal sessions. 

CTRL + ALT + F7 is the GUI and CTRL + ALT + F8 is system.

To copy and paste in Linux, simply highlight the word or phrase you want to copy, that's it, just highlight. Now move to the application you want to paste into, push the middle mouse button, or in the case of a laptop touchpad a two finger tap on the touchpad will paste into the app for you. Simple.

Don't forget that Google is your friend. ;^)

---

### Post by AceRoom on 2010-07-16
I highly agree with digitalcitizen. Especially for a recent migrator, GUI would be much better. Although it is recommened to have only cli for server machines, I don't think that really applies to beginners. Besides, you can install the tools that you need for the machine to be used as a server on top of the GUI.

IMO, it would be easier for the OP to reinstall Ubuntu-Desktop version over the server, then install the server tools. **Advise if you disagree****. I'm not completely sure.** I just thought that he wouldn't have to go through unnessesary tedious steps.

---

