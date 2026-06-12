---
title: "Cannot installed GUI or Desktop"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by InternetDominus on 2009-03-14
Hi,

I just downloaded version 8.10 server, and after installation I tried to install the desktop for graphical interface, however, I get this error message:


```
sudo apt-get install ubuntu-desktp
``` and got message below
```
E: Couldn't find package ubuntu-desktop
```

Then, I tried another command I found somewhere else:

```
apt-get install x-window-system-core xserver-xorg gnenome-desktop-enviroment
```and got message below
```
E: Couldn't find package x-window-system-core
```

Is it that the desktop installation is not on my CD, or am I using wrong commands for version 8.1

Thanks,

ID

---

### Post by labinnsw on 2009-03-14
What?! wasn't the GUI desktop installed with the rest of the distro?

---

### Post by hyper_ch on 2009-03-14
why do you want to install a gui on a server?

---

### Post by Ms_Angel_D on 2009-03-14
> **labinnsw]What?! wasn't the GUI desktop installed with the rest of the distro?[/QUOTE]
The server version doesn't come with a GUI

[QUOTE=hyper_ch said:**
> why do you want to install a gui on a server?
what does this matter it's the OP's Choice.

InternetDominus I believe the command is 
```
sudo aptitude install ubuntu-desktop
```

---

### Post by hyper_ch on 2009-03-14
> **MetalHellsAngel said:**
> what does this matter it's the OP's Choice.

because there's good reasons not to install gui on a server ;)

---

### Post by InternetDominus on 2009-03-14
Actually my goal is to use Xamp with GUI interface, and I thought I had to download the server edition.

Can you please indicate what version to download that I can use with GUI, and xamp or lamp?

Thanks!

ID

---

### Post by hyper_ch on 2009-03-14
if you don't want to run a server, then install desktop or alternate and add the services as you need them. you'll be much better off that way.

---

### Post by theozzlives on 2009-03-14
You mentioned the CD, are you not connected to the internet? The server CD doesn't have the desktop.

---

### Post by InternetDominus on 2009-03-14
Thanks hyper_ch,

So, is server edition like for office server networks or is it for web servers just like what web hosting companies offer? I need for the purpose of running my own website from home.

I read in the features page in the server edition that it comes with php, mysql, etc, so I thought that was the version I needed, but only if I can use GUI because I don't know linux commands yet to run from command prompt

Thanks again

ID

---

### Post by InternetDominus on 2009-03-14
> **theozzlives said:**
> You mentioned the CD, are you not connected to the internet? The server CD doesn't have the desktop.

I meant that I was able to installed from the CD to my hard drive, but when I tried to install GUI, it was a package not found, so I am guessing now from what you guys say, it is not possible to run GUI on server edition.

Thanks,

---

### Post by zvacet on 2009-03-14
Better option is one** hyper_ch** suggested to you and AFAIK it is possible to install desktop on server.

---

### Post by Troll_the_Great on 2009-03-14
> **InternetDominus said:**
> I meant that I was able to installed from the CD to my hard drive, but when I tried to install GUI, it was a package not found, so I am guessing now from what you guys say, it is not possible to run GUI on server edition.

Thanks,

You can run a GUI on a server. The error you got is because either you are not connected to the internet (the package "ubuntu-desktop" is not on the install CD), or you don't have the repositories enabled (but that's highly unlikely). But if you don't plan to run your machine as a server, it's no use installing the server version. Install the desktop version, and then install whatever programs you need for your work.
Hope this helps.
Cheers!

---

### Post by hyper_ch on 2009-03-14
> **InternetDominus said:**
> So, is server edition like for office server networks or is it for web servers just like what web hosting companies offer? I need for the purpose of running my own website from home.
Well, normally you want to install as little on a server as possible because servers usually need their resources for "serving clients". You don't wanna load a gui because it uses more ram. You don't want to run unnecessary daemons (services) because it has an impact on performance. With the ubuntu server edition you install a very basic system and also a different kernel that is aimed as server tasks.

Of course, you can install ubuntu-desktop there but its not contained on the server edition cd. You can easily instally mysel, apache php to it... that stuff is on the server cd.

If you want to truly use a computer as server, then you should not install a gui. You can use it then as media/file/pring/web/email/dns/..... server...

There's not much you need to know about linux commands to setup a server... what you need to know is

- how to travers directories
- how to create/edit/copy/move/delete files
- how to install software from the clie
- how to start/restart/stop daemons
- how to use the man pages

configuration of daemons is done by altering config text files and a gui doesn't help you at all on editing them.

However if you mainly use your computer as desktop and just want to have apache on there because you do some webdesign and want to locally check first, then just install apache, php, mysql in that desktop install.

---

