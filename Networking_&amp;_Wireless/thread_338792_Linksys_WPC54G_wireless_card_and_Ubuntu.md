---
title: "Linksys WPC54G wireless card and Ubuntu"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by livin4messiah on 2007-01-14
So I was wondering how to install a linksys WPC54G wireless card in ubuntu. I understand there is the synaptic package manager, but Am I not Correct, That you need internet access to begin with to use it? And Once I get NDISWRAPPER installed, how do I go about using it? I was not sure if i could use the Add/Remove Utility or not I have not tried it, because 1. I dont know how to use NDISWRAPPER, 2. I am running from a livecd. because If I was to install it, and couldnt Get the internet up, there would be no purpose for it .
So I dont know If I need Internet to get internet or what .

The Card is showing up in the network Settings dialog. It shows the WIRELESS CONNECTION (Eth1), but it says that it is inactive . I tried clicking the activate button, but got the "Could not enable the interface eth1 check the that the settings are correct for this network, and that he computer is correctly connected to it."

I don't know what to do from here, So Any help will be nice. 

Ryan

---

### Post by teaker1s on 2007-01-15
welcome, firstly you have to find out the chipset by either 
terminal
[COLOR="Red"]lspci[/COLOR]
or
[COLOR="Red"]lsusb[/COLOR]

if you want a general idea of how it all works look at this broadcom guide I helped a little with
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by livin4messiah on 2007-01-15
> **teaker1s said:**
> welcome, firstly you have to find out the chipset by either 
terminal
[COLOR="Red"]lspci[/COLOR]
or
[COLOR="Red"]lsusb[/COLOR]

if you want a general idea of how it all works look at this broadcom guide I helped a little with
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")Ther was a list of things, But I think what we are interested in is 


0000:07:00.0 Network Controller Broadcom Corporation BCM4318 [Airforce one 54G] 802.11G Wireless Lan Controller (rev 02)


Ryan

---

### Post by teaker1s on 2007-01-15
okay please follow link below, read it completely then follow it-it's the most reliable way of using wireless and should work perfectly for yours

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

:mrgreen:

---

### Post by livin4messiah on 2007-01-15
> **teaker1s said:**
> okay please follow link below, read it completely then follow it-it's the most reliable way of using wireless and should work perfectly for yours

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

:mrgreen:That Looks like it would fix my issue, possibly, But is there any easier ways to go about it? Me being the noob that I am, and having a pathical fear of commands, and Love my very user friendly GUI, Is there anything else that I could do, or is it a must to do it this way?


Ryan

---

### Post by dmizer on 2007-01-16
there are too many gui interfaces available in ubuntu for us to write howto's which would cater to them all.  a short list includes (but is not limited to): gnome, kde, xfce, icewm.

each of these have different gui ways of doing things, and require different clicks in different places with different program names.  however, each and every one of them work identically via commands.  this is why you will find that most howto's are written with command line instructions.

furthermore, most command line instructions merely require you to copy and paste the command (no typing).

as a noob myself, i would highly suggest you work toward getting past your fear of the command line, as it is an essential tool when using ubuntu.

furthermore, gui commands are much more difficult to write than command line instruction.  for example, here's a command you can copy and paste directly into your command line which will allow you to enable a network adapter:
```
sudo ifup eth0
```

for gnome, the exact same command would require the following instruction:
click on system > administration > networking
type in your password when prompted.
find your eth0 adapter in the list and click on it to select it.
then click on the button on the right that says "activate"
then click on OK.

way too many steps and way too many possibilities for making mistakes, and that doesn't even cover the poor neglected (but certainly popular) kde, and xfce.

if you really need gui only interface, you might want to consider an alternative operating system.  something like [linspire](www.linspire.com) or [mepis](www.mepis.org), but those operating systems are somewhat less robust.

---

