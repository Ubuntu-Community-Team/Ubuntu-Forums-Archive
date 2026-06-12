---
title: "Xubuntu via Wubi on Sony C1"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Data359 on 2009-09-09
Hi Guys a little help please - I am trying to install xubuntu to my travel companion a Sony PCG-C1MGP on a dual boot with Windows XP - as this is my first taster of linux I am trying to load via the Wubi method as my machine has no fixed optical drive etc. I have read up and found that 8.04 has been installed sucessfully. I have downloaded the iso for 8.04.1 lts to my computer on a separate partition which is clean but I would like to know which Wubi to use to install this. Any help would be appreciated please.
 
Thanks

---

### Post by earthpigg on 2009-09-09
if your computer has no optical drive, you will either need to:

1. use ubuntu's 'usb startup disk creator' from another computer that either has ubuntu installed or has it running from an Ubuntu LiveCD to properly apply that .iso file to a thumb drive. this is by far the most conventional easy option, if it is possible for you.

2. use windows software to *mount* the .iso file and run wubi.exe from the virtual cd. i don't have windows, so i can't vouch for the quality of any windows software. if you already have and are familiar with mounting .iso files in Windows (Microsoft is notorious for making this difficult), this may be the best choice.

3. locate and use an .img file that includes wubi, properly put it on a thumb drive, and install from there. this is easy as pie to do in Linux, a bit more involved in Windows.

4. borrow a friends optical drive, put a normal ubuntu cd in, and run WUBI.



choose your destiny, sir.

---

### Post by earthpigg on 2009-09-09
also, i tend to simply say 'ubuntu' for the sake of simplicity. xubuntu **_is_** ubuntu. wikipedia search "desktop enviornment" if that is confusing you :D

---

### Post by natravis on 2009-09-09
> **earthpigg said:**
> 

2. use windows software to *mount* the .iso file and run wubi.exe from the virtual cd. i don't have windows, so i can't vouch for the quality of any windows software. if you already have and are familiar with mounting .iso files in Windows (Microsoft is notorious for making this difficult), this may be the best choice.

This is pretty easy to accomplish. Use [Daemon tools Lite]("http://www.disk-tools.com/download/daemon") to mount the .iso file. Just install and restart when it needs to, then run the program and tell it to create a single drive. Mount the image file through that program then you will be able to access it as if the drive was plugged into your computer. Keep in mind that installing through Wubi will be a little laggy compared to a normal install and you will not be able to share files between Ubuntu and Windows but it is definitely a good way to try it out.

Enjoy!

---

### Post by earthpigg on 2009-09-09
[http://en.wikipedia.org/wiki/Daemon_tools#Blacklisting](http://en.wikipedia.org/wiki/Daemon_tools#Blacklisting)

we don't want to make windows unusable or unstable for him.


sure, daemon tools will work now... and when the next generation of Digital Restrictions Management comes out and he buys some non-free software that includes it, that non-free software attempts to remove DT's rootkit, and ends up borking windows? 

he then calls that company, who then blame microsoft, who then blame daemon tools, who then blame the company behind the new software he just installed, and none offer him any solutions -- except, of course, to purchase the latest version of Microsoft Windows and do a fresh install of not only windows, but also Ubuntu?


bleh. bunch of greedy self-serving a-holes.

hence, i refuse to vouch for *any* non-free software.

but yes, data359, Daemon Tools _**may**_ work. among other possibilities.

:D

---

### Post by natravis on 2009-09-09
Fair enough, I have only had one problem with Daemon Tools Lite and that was a Win7 compatibility issue. An open source alternative that is recently updated is available at [http://wincdemu.sysprogs.org/](http://wincdemu.sysprogs.org/). I can't vouch for it because I have never used it but it definitely seemed simple enough from looking at the screenshots.

---

### Post by Data359 on 2009-09-10
Hi guys sorry at work today so only just had chance to reply:  
 
Thanks for all your advice - however I am now a little more confused.  My aim with using Wubi was to be able to try xubuntu without the need to mount the iso and to have as little pain as possible.  I have managed to follow the instructions on the wubi site to install the wubi exe to my clean partition in windows and then run and install the 8.456 version of unbuntu which I have had working well on the Sony via Wubi (which means I can then remove through add/remove programmes in windows).  However after a little more research I discovered that xubuntu would be the desktop to use as it has more support for the older machine and also that it had been run successfully on my model.  To get the stable version I have downloaded the lts 8.04.1 iso from the xubuntu site which wubi will use in place of its own downloaded version if it is present in the same folder - however there is no corresponding wubi loader in the previous versions list on the wubi site - here [http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)
 
Apologies for the newbie type indecision but as I am about to go on holiday for a couple of weeks - I would like to take xubuntu with me to play with but still have my windows for mail etc until I get everything sorted.

---

### Post by earthpigg on 2009-09-10
o, well that is a much simpler question.

> sudo apt-get install xubuntu-desktop

log out. 

at the login screen, select 'session -> xubuntu'

---

### Post by ottosykora on 2009-09-10
> **Data359 said:**
> I have downloaded the iso for 8.04.1 lts to my computer on a separate partition which is clean but I would like to know which Wubi to use to install this. Any help would be appreciated please.
 
Thanks

well as you want just install with wubi:
there where you downloaded the iso file, the ftp site, just scroll down and you will find file called wubi.exe. Fot the 8.04 it will have size of abt 957kb.
( [http://mirror.switch.ch/ftp/mirror/ubuntu-cdimage/8.04/](http://mirror.switch.ch/ftp/mirror/ubuntu-cdimage/8.04/) for example)

Just place the iso file (must be desktop version) and the wubi file in same folder and run double click on the wubi file.
All the rest is self explaining, follow the instructions on the screen. 
It will make folder called ubuntu or xubuntu etc and create all files in it.

If you pick wrong wubi for your iso, it will tell you during the installation, so you can not make anything wrong.

---

### Post by Data359 on 2009-09-10
Hi guys thanks for all your help - wubi loaded and running as we speak with xubuntu iso for lts.
 
:)

---

### Post by ottosykora on 2009-09-10
hmm, sometimes the simple way is the most efficient one...

---

### Post by earthpigg on 2009-09-10
> **ottosykora said:**
> hmm, sometimes the simple way is the most efficient one...

he overloaded his original question with all sorts of stuff that threw me off and made it hard to understand what he wanted, lol.

---

