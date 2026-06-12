---
title: "Catch 22 - fixing Internet without the Internet"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by Ethelbert2 on 2007-02-20
[FONT="Georgia"][COLOR="DarkGreen"][SIZE="3"]I have been chasing around for days to get my wireless card working - it has an rtl 8185 chipset and freezes everything up - eventually I have given up and changed it for a Broadcom one in my main computer  (8185 works fine in XP so it will be fine as an alternate there). Good instructions to get Broadcom going are posted.  (eg    [www.ubuntuforums.org/showthread.php?t=319402&highlight=broadcom+4306+airport](www.ubuntuforums.org/showthread.php?t=319402&highlight=broadcom+4306+airport)) and (ubuntuforums.org/showthread.php?t=185174)

But I am stuck. 

The first part of those instruction says that "using an Internet connection" you have to get a programme called bcm43xx-cutter (it removes firmware from windows drivers for use with the Linux one).

But this is like Joseph Hellers famous Catch 22.  I want to connect to the Internet by making my wifi card go. But to make my wifi card go I have to connect to the Internet. AND NO I DON'T HAVE ANY OTHER WAY TO DO IT I already learned that Linux won't support the modem (more days) , :mad: and the old computer has no Ethernet. Why do all the advice guides assume that I will have these things?

MY only option is to get bcm43 etc from the Internet on a Win XP computer and move it over. But that begs questions.:confused: 

Where do I find it? (Googling does not give a result). What version do I need (I have Ubuntu 6.10). Even if I do find it, how do I make Synaptic or apt-get find it and install it?  (I am essentially a total beginniner so what I mean is - where do I need to put the file and what instuctions do I need to put in).  Will I have to get other stuff at the same time? 

IF I can get that installed then I might be OK with the remaining instructions I have found. 

It is very frustrating - I really want to use this OS, and like the look etc and playing with the basics. But wireless is the "killer app" (in this case meaning it kills off all possibility of using it, especially as dialup will not work EITHER).


[/SIZE][/COLOR][/FONT]

---

### Post by chili555 on 2007-02-20
You can find it here: [http://packages.ubuntu.com/edgy/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/edgy/utils/bcm43xx-fwcutter)

I think you can download it from any old XP box and save it to a USB stick, Move back to the Ubuntu machine and you will have a .deb file. Issue the command sudo dpkg -i <file_to_install>.deb.

You may need other files and just follow the same process, cumbersome as it is.

---

### Post by Ethelbert2 on 2007-02-21
[COLOR="DarkGreen"][FONT="Georgia"][SIZE="3"]Multiple thanks - hopefully I can work this out[/SIZE][/FONT][/COLOR]

---

### Post by miakeru on 2007-02-24
> **Ethelbert2 said:**
> [COLOR="DarkGreen"][FONT="Georgia"][SIZE="3"]Multiple thanks - hopefully I can work this out[/SIZE][/FONT][/COLOR]

Have you worked this out yet? I've got a laptop with an RTL 8185 chipset and have had *zero* luck getting it to work in any distro. I've actually made it able to find and attempt to connect to wireless networks, but once it does connect it freezes up entirely.

I'd love to get this working in Ubuntu, but without wireless I'd have a useless Linux installation.

If you do get this working, please reply and let us know how you did it. I know that I and many other would be interested in this. Thanks in advance!

---

### Post by Ethelbert2 on 2007-02-28
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]
Excuse the delay replying but I had a separate telephone issue. (Nothing to do with cards) and could not connect.

Anyway --- 
The rtl 8185 is [COLOR="DarkOrange"]a **disaster**[/COLOR] - very frustrating and I could not get it working by any suggested methods, neither wrapping it nor using the supposed Linux driver (I got as far as getting that to load in but the card still froze the whole system every time I tried to connect.) 

But I am ***ecstatic*** neverthless.

The Broadcom (in a Bufalo card I bought) has been a different story altogether, if a bit time consuming.  

After much hunting I found a variety of sources of advice on the Ubuntu and PCLinux forums - first to get the Win driver (which was listed at an easily found location) and extract the firmware for the card using a prgramme called BCM43xx-fcutter which is relatively easily downloaded, it seems, if you have an Internet connection.

I had an extra problem because the intstruction all depended on using an internet connection (Catch 22) so I faced a difficult task  - I found things but did not know what to do anyway (I downloaded it elsewhere and then moved it on a usb flash mem drive). Eventually got Chili555's answer (thanks a million) answer for downloading via Windows along with various packages it depends on and how to install thise first before then followoing the insructions. 

Looked like it was going to be a long task however and then suddenly I found that someone had posted **the firmware itself**, already extracted, (for the 4306)  and simple instructions for loading it (from a deb file). This shortcircuited all the process of  installing the cutter programme and its dependencies.

So I tried simply installing the deb file. 

**And it worked!!!!**

The card suddenly came alive - configured like a dream and lo and behold I was connected.

**Brilliant.!!!** After two weeks it was like having the dentist finally remove a bad tooth.

Synaptic came alive. UPdates were downloaded. I can experiment with Linux now to my heart's content.  Currently using Xubuntu.

(Next isssue getting various other things going - there is a way to do printing using the Livebox router which I have to work out from both the XP machine and then the Linux).

I have a couple of other issues to finally sort out. Currently my network is set to use a WEP key but has "open" rather than "shared" for the "network authentication" setting (I am referring back to my Win XP computer to tell you this). That setting is faintly worrying and  I am not sure what it means since it is at least ALSO asking for the WEP key.

But since it is at least working I don't want to mess too much yet.

But boy - it makes all the difference between wall kicking frustration and calm.


Here are some links ----

This was good

[http://www.ubuntuforums.org/showthread.php?t=319402&highlight=broadcom+4306+airport](http://www.ubuntuforums.org/showthread.php?t=319402&highlight=broadcom+4306+airport)

and this 
:
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

(seems to be the first posting suggesting the cutter and has a long long discussion)

[http://ubuntuforums.org/showthread.php?t=178424](http://ubuntuforums.org/showthread.php?t=178424)

[http://www.pclinuxos.com/forum/index.php?topic=8631.0](http://www.pclinuxos.com/forum/index.php?topic=8631.0)



I cannot remember from which forum I found the link to the already cut out firmware file but if you need that I could send it to you.


Meanwhiole I have a second card which I tried on another old computer - this was a Wireless 108G PCI Air Plus XtremeG D-Link. It has an Atheors chipset and was found automatically during Xubuntu install and configured using the wizard. 

I am about to try it out connecting properly.









 [/FONT][/SIZE][/COLOR]

---

