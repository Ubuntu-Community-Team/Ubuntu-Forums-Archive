---
title: "Flash player issues."
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Krullivan on 2009-02-22
I've installed the flash player via adobe's website through the .tar.gz package. But when I play a video from Youtube, Hulu, etc. it will play fine for a few seconds, freeze and start playing again. any help? 

Thanks in advance :popcorn:

---

### Post by thecrimsonalchemist42 on 2009-02-22
What web browser are you using?

---

### Post by Krullivan on 2009-02-22
The default, firefox

---

### Post by Lithical on 2009-02-22
Open a Terminal (Applications > Accessories > Terminal) and start Firefox through it by typing simply "firefox" (without quotes, of course) and go to your site to watch your video.  If an error message is output in the terminal when your browser starts freezing, copy and paste that message here to be analyzed.

---

### Post by Krullivan on 2009-02-22
Nothing output, but the entire flash media starts freezing / lagging.

---

### Post by Lithical on 2009-02-22
Maybe you should check if any of this applies to you:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb407510&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb407510&sliceId=2)

I've been using Ubuntu for about a week so I am just learning the ropes myself, I'll see if I can dig up anything else :)

---

### Post by Krullivan on 2009-02-22
nope, none of it applys to me.

---

### Post by Lithical on 2009-02-22
Maybe you should try reinstalling via the package manager to make sure no dependencies are missing, or the .deb from Adobe's site which will install itself.

---

### Post by Krullivan on 2009-02-22
i've tried it without luck :(

---

### Post by sandyd on 2009-02-22
say, what graphics card are you using?

installed any drivers for it lately?

---

### Post by Krullivan on 2009-02-22
How would I go about finding out what graphics card i'm using?

EDIT: on a dell dimension 2400

---

### Post by PRC09 on 2009-02-22
Hi Folks,
   I followed these instructions and it works fine .Hope this helps.There is a hotlink that says flashplugin non free click here to install and it worked perfectly........





[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

---

### Post by sandyd on 2009-02-22
> **Krullivan said:**
> How would I go about finding out what graphics card i'm using?

EDIT: on a dell dimension 2400
nvm that guy right under your post... you got flash player installed properly, but you seem to have somevideo problems... (yes, sorry, i'm feeling mean today)

type this in the terminal

```

lspci

```copy that and paste it here

---

### Post by Krullivan on 2009-02-22
kyle@Lintop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
kyle@Lintop:~$

---

### Post by sandyd on 2009-02-22
read here
[http://ubuntuforums.org/archive/index.php/t-256470.html](http://ubuntuforums.org/archive/index.php/t-256470.html)

it could be for 1 or more reasons...

1. your xorg.conf needs some editing (post it here and ill fix it)
open it by
```

sudo gedit /etc/X11/xorg.conf

```2. You haven't set enough video memory in the BIOS
in the BIOS, you may have an entry that allocates memory to the integrated video. Mine had options for 1MB and 8MB (where 1MB limited me to ridiculously low resolutions and 8MB opened that up considerably).

there! another problem solved.

everyone says the resolution is crap on that card so i guess that it is your resolution that is the problem. with the video freezing, its a sign of not enough video RAM.


P.S. Try option #2 first!

---

### Post by JerichoKru on 2009-02-23
Why did you use the tar.gz when there is a .deb availible?

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

click the dropdown and select the DEB package and install that.

EDIT: whoops, I read what's above my post....whatever

---

### Post by Krullivan on 2009-02-23
The problem seemed to have solved itself

---

