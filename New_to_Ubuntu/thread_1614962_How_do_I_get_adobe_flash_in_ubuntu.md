---
title: "How do I get adobe flash in ubuntu?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by shades9323 on 2010-11-06
I have the latest version, 10.10 I think running in virtualbox and again in vmplayer.  I would like to get the adobe flash but don't know what to do after the download has concluded.  I have never used Linux until now.  Thanks for the help,

Scott

---

### Post by ubunterooster on 2010-11-06
Go to a flash site such as youtube. near the top of the browser (right below the tabs) will be a prompt to install missing plugins. Just follow the instructions and restart Firefox when asked to do so

---

### Post by thunk77 on 2010-11-06
Hello and welcome!

Open up a Terminal (Located in Applications -> Accessories ->Terminal)

Enter the following:

```
sudo apt-get install ubuntu-restricted-extras
```

It will ask you for your password (don't worry that when you're typing it doesn't show on the screen, it's a security thing)

Hit enter. It will ask you if you want to install a bunch of packages by entering y for yes and n for no. Enter y and then hit enter again.

This procedure will pull in support for flash as well as a bunch of other useful stuff like mp3 support, rar support, java etc.

Application installation procedure is quite different from windows so I suggest a little bit of reading (don't worry there's pictures and videos too!)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://screencasts.ubuntu.com/MoS2007/12_Installing_Applications](http://screencasts.ubuntu.com/MoS2007/12_Installing_Applications)

Regards

---

### Post by shades9323 on 2010-11-06
> **ubunterooster said:**
> Go to a flash site such as youtube. near the top of the browser (right below the tabs) will be a prompt to install missing plugins. Just follow the instructions and restart Firefox when asked to do so

Worked great, thanks.  This site will be a valuable resource for me in learning Linux.

---

### Post by ubunterooster on 2010-11-06
No problem; I am glad to have helped :D

---

### Post by vishnuscorpion on 2010-11-25
> **thunk77 said:**
> Hello and welcome!

Open up a Terminal (Located in Applications -> Accessories ->Terminal)

Enter the following:

```
sudo apt-get install ubuntu-restricted-extras
```

It will ask you for your password (don't worry that when you're typing it doesn't show on the screen, it's a security thing)

Hit enter. It will ask you if you want to install a bunch of packages by entering y for yes and n for no. Enter y and then hit enter again.

This procedure will pull in support for flash as well as a bunch of other useful stuff like mp3 support, rar support, java etc.

Application installation procedure is quite different from windows so I suggest a little bit of reading (don't worry there's pictures and videos too!)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://screencasts.ubuntu.com/MoS2007/12_Installing_Applications](http://screencasts.ubuntu.com/MoS2007/12_Installing_Applications)

Regards
when i run the comand,it says like this:
[FONT=monospace]E: Couldn't find package ubuntu-restricted-extras



wht to do?
[/FONT]

---

### Post by mikewhatever on 2010-11-25
> **vishnuscorpion said:**
> when i run the comand,it says like this:
[FONT=monospace]E: Couldn't find package ubuntu-restricted-extras



wht to do?
[/FONT]

Installing the ubuntu-restricted-extras just to get flash is an overkill. Just search for 'flash' in the Software Center or download the installation file in .deb format from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/).

---

### Post by gandaran on 2010-11-25
> **vishnuscorpion said:**
> when i run the comand,it says like this:
[FONT=monospace]E: Couldn't find package ubuntu-restricted-extras



wht to do?
[/FONT]
update the software package list
```
sudo apt-get update
```

---

### Post by vishnuscorpion on 2010-11-25
> **gandaran said:**
> update the software package list
```
sudo apt-get update
```
@mikewhatever&gandaran:thanks for ur answers..i updated the software package as well as installed the flash plugin(.deb format)...:)
ur advices were highly useful..hope in future too..may i ask one more!!
wht's the difference b/w the flash plugin in **.deb** format and **APT **for **9.04 **and above distros

---

### Post by rusty149 on 2010-11-25
.deb is a package file to install software. (Equivalent to .exe for windows and .dmg for mac). 
 
APT is a program that finds, downloads and installs .deb packages from sources.

---

