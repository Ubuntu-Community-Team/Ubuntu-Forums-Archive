---
title: "Ubuntu is screwing up and not working right..Gdebi won't work.. PLEASE READ!!"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-19
Okay, I just installed Ubuntu 8.10, and got my wireless working not too long ago. Some things will work, like my internet, appearance preferences, games and a few other things. Its a little slow, my gdebi installer is not working at all.. If I try to install limewire or adobe flash player, the installer just never pops up, and it won't do it if I click open with gdebi either. My update manager won't work, I click it and nothing happens. My software sources won't work either.. A lot of things don't work. I just click it and nothing happens... What can I do? Can I do something in the terminal or what? 
Help, I'm trying to get away from Windows, but now this thing won't even work :(..

---

### Post by kyeh on 2009-01-19
try this command

```

sudo apt-get update

```

It may give some output regarding why it's not working:popcorn:

---

### Post by gymophett on 2009-01-19
> **kyeh said:**
> try this command

```

sudo apt-get update

```

It may give some output regarding why it's not working:popcorn:

I tried.. It gave me this.. and it's still not working


```

Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://security.ubuntu.com intrepid-security/main Packages      
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done

```

:confused:

---

### Post by deadmnky on 2009-01-19
now try 
[B]sudo apt-get upgrade 
[/B]
it should do your update

i believe the terminal commands to install your packages are
**sudo dpkg -i <filename>**
not 100% sure as i do the graphical way and if yours is not working it may help
you can also type **man dpkg** and it will tell you which variables they are

---

### Post by yeats on 2009-01-19
deadmnky's got it right.  You would do well to learn to do this on the command line.  It's not difficult and will almost always work, even when the graphical tools fail.  (It at least gives you debugging information that the graphical tools don't).

---

### Post by gymophett on 2009-01-19
> **deadmnky said:**
> now try 
[B]sudo apt-get upgrade 
[/B]
it should do your update

i believe the terminal commands to install your packages are
**sudo dpkg -i <filename>**
not 100% sure as i do the graphical way and if yours is not working it may help
you can also type **man dpkg** and it will tell you which variables they are

Thanks.. It seems to be working because the download is going to take a little over an hour... Although I'm not exactly sure what you mean by this?
Can you explain to me a little bit. I'm so new to Linux. Sorry :/

> 
i believe the terminal commands to install your packages are
**sudo dpkg -i <filename>**
not 100% sure as i do the graphical way and if yours is not working it may help
you can also type **man dpkg** and it will tell you which variables they are

---

### Post by yeats on 2009-01-19
apt-get is the command line utility you use to manage packages - you must run it as the superuser, which in Ubuntu means you preface all commands with "sudo" which prompts you for your password (you have to type sudo each time - the system doesn't "remember" this for you - you get used to it)

To update the package lists (which you'll want to do each time you do an update/upgrade/install):

```
sudo apt-get update
```

To perform an upgrade of all available packages:

```
sudo apt-get upgrade
```

To add a package by name:

```
sudo apt-get install *package*
```

To uninstall:

```
sudo apt-get remove *package*
```

Those are the basics - you can learn more by typing

```
man apt-get
```

which will list all the options for this.

Hope that helps.

---

### Post by gymophett on 2009-01-19
> **chrissharp123 said:**
> apt-get is the command line utility you use to manage packages - you must run it as the superuser, which in Ubuntu means you preface all commands with "sudo" which prompts you for your password (you have to type sudo each time - the system doesn't "remember" this for you - you get used to it)

To update the package lists (which you'll want to do each time you do an update/upgrade/install):

```
sudo apt-get update
```

To perform an upgrade of all available packages:

```
sudo apt-get upgrade
```

To add a package by name:

```
sudo apt-get install *package*
```

To uninstall:

```
sudo apt-get remove *package*
```

Those are the basics - you can learn more by typing

```
man apt-get
```

which will list all the options for this.

Hope that helps.

Thanks.. I did the upgrade, now my computer doesn't even let me get online :'(

---

### Post by jrusso2 on 2009-01-19
What I would suggest first is to run gdebi from the terminal and see if there are any errors and post the errors here.

open a terminal window and enter gdebi-gtk

---

### Post by deadmnky on 2009-01-19
the **sudo dpkg -i** is the command to run debian package manager from the command line
the **<filename>** was the name of said package you are trying to install. limewire and flashplayer
so you would type 

**sudo dpkg -i install_flash_player_10_linux.deb** 

for the adobe one i am not sure about the limewire as i dont use it but if it is a deb you can type the same thing just replacing the name of adobe file with lime file
i forgot to mention you have to be in the directory where you downloaded the files to for example i always use my desktop so i would

cd /home/deadmnky/desktop 

to get there then run the dpkg command

glad that helped and hope i explained my self some more
if you have any more questions i will answer what i can

---

