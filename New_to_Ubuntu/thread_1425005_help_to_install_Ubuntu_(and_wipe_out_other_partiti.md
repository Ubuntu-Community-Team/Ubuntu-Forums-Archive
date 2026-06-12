---
title: "help to install Ubuntu (and wipe out other partitions)"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by oingk on 2010-03-08
Hi friends.
 
I have windows XP (in addition to a small partition dedicated to backing up my system) and now I want to wipe out all these and install Ubuntu 9.10.
 
So I downloaded and created a DVD with Ubuntu and when I insert it and start my computer I get a menu  with the following options:
 
-Install Ubuntu Server
-Install Ubuntu ...... (something that I don't remember)
-Check disk for defects
-Test memory
 
and maybe a couple more.
 
what should I chose in my case?
 
Also, I was dual booting with Ubuntu before and starting my computer via Grub2. Is there a way to now make my Ubuntu fire up as soon as I switch my computer on, without going through Grub2 menu? Or would this be not a good idea?
 
thanks

---

### Post by halitech on 2010-03-08
Unless you want a command line version, you don't want Ubuntu server. My guess would be the second option but without knowing exactly what it is, I'm guessing. You may want to run the check disk for defects option before trying to install just to make sure it is okay.

As far as Grub, you need grub in order to get the system to boot. It's a boot loader that starts the process of actually loading the OS.

---

### Post by oingk on 2010-03-08
[IMG]http://i.cmpnet.com/bmighty/images/slideshows/20090116/wintolinserver_slide01.jpg[/IMG]
 
It was the same as this photo, only there was an additional second choice. I believe it was "Install Ubuntu Graphics something"
 
EDIT: Actually it wasn't something about Graphics. It was "**Install Ubuntu Enterprise Cloud**"

---

### Post by oingk on 2010-03-08
OK I get it about GRUB, but can't I make it to not go through the menu when starting up? and just go in Ubuntu automatically? or is that not a good idea?
 
in regards to what the second option was, I will check right now and let you know. it will only take a couple of mins.

---

### Post by halitech on 2010-03-08
you can set the time out to a low number like 1 second but it will have to at least load.

---

### Post by oingk on 2010-03-08
OK.
Second option is "**Install Ubuntu Enterprise Cloud**"
 
So which option should I chose?

---

### Post by mosshorn on 2010-03-08
Question: Did you want the server OS?

---

### Post by halitech on 2010-03-08
Ummmm you don't want either. From what I can find out, Ubuntu Enterprise Cloud is a server system designed for cloud computing (see here - [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall) ) not for desktop use. You want to get the desktop ISO from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by oingk on 2010-03-08
halitch thanks, but can you find the respective one for 64bit?
 
mosshom, I don't know what the server OS is.

---

### Post by halitech on 2010-03-08
Click on the link for Alternative download options, including Ubuntu installer for Windows and select 64bit.

The server OS is as I said, command line only and used on servers

---

### Post by da burger on 2010-03-08
> **oingk said:**
> halitch thanks, but can you find the respective one for 64bit?
 
mosshom, I don't know what the server OS is.

From my understanding Ubuntu server is that same as Ubuntu desktop but it does not come with graphics or the same pre-installed programs. This is probably not want you want as I think you are installing for home use.

To get 64bit go to [the same page]("http://http://www.ubuntu.com/getubuntu/download") as halitech said, click > Alternative download options, including Ubuntu installer for Windows and select 64bit before clicking download.

---

### Post by oingk on 2010-03-08
ok then I guess I don't want the server one.
 
Thanks, I am downloading now the Ubuntu 64.
 
Hopefully whan I start it up there will be different options than the ones I described, I'll come back and let you know.

---

### Post by halitech on 2010-03-08
> **da burger said:**
> From my understanding Ubuntu server is that same as Ubuntu desktop but it does not come with graphics or the same pre-installed programs. This is probably not want you want as I think you are installing for home use.


close but 1 main difference. The server version has a server kernel which is designed to run better in a server situation where multiple apps will be run at a time. I believe it also allows for more then 4gig of ram (on 32bit systems) where the desktop version doesn't without using PAE.

---

### Post by da burger on 2010-03-08
> **halitech said:**
> close but 1 main difference. The server version has a server kernel which is designed to run better in a server situation where multiple apps will be run at a time. I believe it also allows for more then 4gig of ram (on 32bit systems) where the desktop version doesn't without using PAE.

Thanks I didn't know that (although I assumed there were some technical differences I wasn't aware of).

---

### Post by oingk on 2010-03-08
hi, the thing worked out fine, I installed ubuntu, thanks.

---

