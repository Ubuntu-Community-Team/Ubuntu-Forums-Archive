---
title: "Help Connecting to wireless net with Ubuntu 9.10"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by NSXTypeR on 2009-11-17
Well I have a Dell Inspiron 1525 and fought to get my wifi card installed and got all that up and running. Only problem is when I click to connect to my wireless net it never shows up, in fact nothing does here is a screen shot of what I see. I'm really new to this just got the CD for it yesterday. Any help is very much appreciated. I am also using a duel boot with Windows XP and Ubuntu if that makes any difference. Thanks [IMG]http://i604.photobucket.com/albums/tt124/NSXTypeR1989/WirelessConnection_.png[/IMG]

---

### Post by sandyd on 2009-11-17
this may sound stupid, but have you tried right-clicking on the network icon?

---

### Post by NSXTypeR on 2009-11-17
Yes I have and it shows all the different styles of connection I.E. Wireless, DSL, VPN and so on. But I can never find my wifi connection. I know its not hidden and shows up, I do have the code and all but can't find the network.

---

### Post by Redmage913 on 2009-11-17
What is your wireless card?

---

### Post by NSXTypeR on 2009-11-17
It was a Broadcom BW43 Something, Sorry can't remember a bunch of letters and numbers off the top of my head. But I know its installed and should work. When i first installed Ubuntu, at the top It just showed a signal strength at nothing and never Showed the two comps at the top with the X on em.

EDIT*: Well I did some looking and found the Wireless cards name. Its Broadcom Corporation BCM4312 802.11b/g (rev 01). I don't know how to check if the driver is installed for it and if anyone could help me out I would appreciate it more than you know. Thanks

---

### Post by NSXTypeR on 2009-11-17
Sorry for double post but really need this to work. If any one can help I would really really appreciate it.

---

### Post by Dude-PWB- on 2009-11-17
Check lspci -vv from the terminal and post your network info.

---

### Post by Dvdre on 2009-11-17
> **NSXTypeR said:**
>  Its Broadcom Corporation BCM4312 802.11b/g (rev 01).

That Broadcom driver is a tricky install. I have a Dell laptop with the same wireless card. The problem is that Ubuntu does not recognize the card at all and you won't have a driver after you start running Ubuntu. Thus, no wireless.

To fix it you are going to hardwire connect into a router so you can establish an Internet connection.

I think this thread gives you the steps:

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

fwcutter did the trick for me, but that was 9.04 not 9.10

---

### Post by anewguy on 2009-11-17
And, if you need fwcutter, or ndiswrapper and utils, they are all on the LiveCD.  You have to navigate to the folder "pool/main", from there they are structured like the old disk sets with little in them, but ndiswrapper and utils are in the "n" subfolder - that might be where I saw fwcutter as well (I did see it in one of the subfolders).

The first thing I would do is check under system/administration/hardware drivers and see if it shows a restricted driver installed for your wireless.  You can also open a terminal window (applications/accessories/terminal) and do the lspci -vv as per Dude-PWB-.  You will need to look for the group of lines about your wireless adapter - post back what it says after the "kernel modules".

There are also MANY posts in this forum, and on the net in general, about getting your wireless adapter working with Ubuntu - you may want to search and read those to familiarize yourself more with what needs to be done and how to do it.

Dave :)

---

### Post by s9032g@comcast.net on 2009-12-05
If you have not already done so, connect to the internet with a wired connection; System, Administration, Hardware Drivers. A window will come up showing available drivers for wireless. Since you cannot connect with wireless, whatever shows should say "not activated" pick one (try Broadcom STA) and click on "activate". Your computer will search out the driver on line, install it, and then ask you to restart. If the driver you chose does not activate, then try another one if listed.

When the restart is over double click on the faint little symbol to the left of the speaker emblem on the top bar. Be sure that both wired and wireless show up and are activated. You can rt click on that same symbol to be sure that automatic search for wireless is checked.

SteveG  Been there done that

---

