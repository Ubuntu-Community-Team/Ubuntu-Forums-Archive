---
title: "Ubuntu can access internet, but XP can NOT connect internet"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by niwa on 2010-04-15
Hi, I am a newbie, just installed ubuntu 8.04

Ubuntu is now working normally, e.g. access internet, etc. I can boot Ubuntu or XP,

but XP can not connect internet. (can NOT find Start --> Local Area Connection setting

even though
I re-installed XP several times, 
remedy winsock, install Fix-winsock.reg, 
remedy TCP/IP, installed XPtcprep.exe

Why this happened?  Ubuntu and XP shared the one and same Hard Disk (Ubuntu Sda1, Sda5, XP sda3)?

Please help.
I search internet, there are some similar questions, but no answer.

---

### Post by NewsephJewallz on 2010-04-15
> **niwa said:**
> Hi, I am a newbie, just installed ubuntu 8.04

Ubuntu is now working normally, e.g. access internet, etc. I can boot Ubuntu or XP,

but XP can not connect internet. (can NOT find Start --> Local Area Connection setting

even though
I re-installed XP several times, 
remedy winsock, install Fix-winsock.reg, 
remedy TCP/IP, installed XPtcprep.exe

Why this happened?  Ubuntu and XP shared the one and same Hard Disk (Ubuntu Sda1, Sda5, XP sda3)?

Please help.
I search internet, there are some similar questions, but no answer.

This is down to an 'Anti-Microsoft' feature built into the latest Ubuntu builds which delete certain files on your Windows XP install if it happens to be on the same hard drive. Sorry, just stick with Ubuntu.
:guitar:


-
Newseph Out.

---

### Post by e4uforums on 2010-04-15
Are you using wired or wireless internet in XP?  If you are trying to use wireless, can you access the internet if you use wired internet?  Or, the other way around?

Are you able to ping a web server like Google?



P.S.  Newseph... AWESOME, just AWESOME man!  :)

---

### Post by undecim on 2010-04-15
> **NewsephJewallz said:**
> This is down to an 'Anti-Microsoft' feature built into the latest Ubuntu builds which delete certain files on your Windows XP install if it happens to be on the same hard drive. Sorry, just stick with Ubuntu.
[/joke]

Is there anything special about the way your network is set up? Do you connect to a router, or directly to a cable modem, or some other connection?

---

### Post by niwa on 2010-04-15
> **NewsephJewallz said:**
> This is down to an 'Anti-Microsoft' feature built into the latest Ubuntu builds which delete certain files on your Windows XP install if it happens to be on the same hard drive. Sorry, just stick with Ubuntu.
:guitar:


-
Newseph Out.

1) my ethernet is wired direct to modem

2) Ubuntu lshw identified every components normal
    thus, ethernet card, graphics card, etc are all OK.

3) Ubuntu can access internet connection.

4) I just disconnected the Hard Disk of Ubuntu/Xp, and replaced it with another Hard disk --

    then reinstalled XP on this new hard disk
    (format and complete install)

     once again,
   this newly installed XP on new Hard disk still can NOT connect internet!

5) should I take apart components and re-assemble them ?

.

---

### Post by spcwingo on 2010-04-15
Did you install the driver for your network card on XP?

---

### Post by srs5694 on 2010-04-15
You mentioned a modem. What type of modem is this? (Cable, DSL, or something else?) Many DSL providers use something called PPP over Ethernet (PPPoE), which requires special OS-side configuration. If you're using this, it's conceivable that Ubuntu set it up correctly automatically or semi-automatically but XP didn't. If so, you'll need to track down the XP configuration tools for PPPoE (sorry, I can't help) or contact your ISP for help. If I'm right, this is really an XP problem, completely unrelated to Linux.

Since it works in Linux, this is almost certainly not a hardware problem so you shouldn't need to fiddle with the hardware.

If you're unsure what's going on, you could try posting the output of the "ifconfig" command in Linux. That'll tell us what your network connections are.

Incidentally, connecting directly to the Internet is usually a bit risky. You're better off using a broadband router, which includes some firewall-like features. Ubuntu's pretty secure by default, but it's better to be safe than sorry. That said, some DSL and cable modems include built-in firewall features, so this may not be necessary; it's hard to say without knowing more about your hardware. Also, if you're currently using PPPoE and you add a broadband router, you'll have to reconfigure Linux's network connection.

---

### Post by dineshs on 2010-04-16
In XP
start-settings-control panel-network connections
OR
open my computer - rightclick my network places and click properties
Now what is the status of Local area connection?Is there one?

---

### Post by niwa on 2010-04-16
Hi, everyone,

After days and nights of efforts taking your comments into consideration,
I managed to reinstate XP's internet connection
It is so simple, i.e.
just re-installed motherboard drivers and ethernet drivers
and that is it.  XP can access internet now!

and Ubuntu is still in good shape!
All this mess has nothing to do with Ubuntu!

Thanks for all of you.

..

---

### Post by niwa on 2010-04-17
> **niwa said:**
> Hi, everyone,.......

and Ubuntu is still in good shape!
All this mess has nothing to do with Ubuntu!
Thanks for all of you.
..

[QUOTE=NewsephJewallz 	 		**Re: Ubuntu can access internet, but XP can  NOT connect internet**

......... the latest  Ubuntu builds which delete certain files on your Windows XP install if  it happens to be on the same hard drive. 

.[/QUOTE]

It is possible that Ubuntu did DELETE certain files on XP.
That is why I have to re-install Motherboard and Ethernet drivers?

..

---

### Post by praveenthivari on 2010-04-17
> **niwa said:**
> It is possible that Ubuntu did DELETE certain files on XP.
That is why I have to re-install Motherboard and Ethernet drivers?

..

wat a stupid logic!!!:):):)

---

### Post by srs5694 on 2010-04-17
> **niwa said:**
> It is possible that Ubuntu did DELETE certain files on XP.
That is why I have to re-install Motherboard and Ethernet drivers?

..

No -- or at least it's very unlikely. NewsephJewallz's comment was, I believe, intended as a joke -- a very bad joke, in the sense of being easily misinterpreted as a real suggestion.

I posted a serious reply with some suggestions earlier. I suggest you review it.

---

### Post by HermanAB on 2010-04-17
Howdy,

The simple moral of the story is that you need to run the MS Windows Device Manager and resolve all issues there, conveniently marked with little yellow flags, before trying to continue with the system configuration.

---

### Post by inso_741 on 2010-04-25
> **niwa said:**
> It is possible that Ubuntu did DELETE certain files on XP.
That is why I have to re-install Motherboard and Ethernet drivers?

..


the only change that ubuntu does to your xp install is it replaces the bootloader with grub, rest of the OS is untouched
your problem is that you probably just forgot to install those drivers for your ethernet adapter thats it....:)

---

