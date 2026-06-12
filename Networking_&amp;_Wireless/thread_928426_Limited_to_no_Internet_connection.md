---
title: "Limited to no Internet connection"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by chadwcureton on 2008-09-24
Hi everybody.  I am new to Ubuntu and I am having an issue getting my internet to work on a consistent basis.  I have loaded the OS on an older laptop, 2 years old or so, while I do the research on my desktop and see if I can get it working effectively enough for me to give up Vista Ultimate, which I want to do.  My network gear is as follows:

Netgear WGT624 v3

Ethernet Interface: RTL8111/8168B PCI Express Gigabit Ethernet controller. Driver r8169

Wireless: TR2561/RT61 802.11g PCI.  RT61 driver.  logical name is wmaster0

I am able to browse the internet for a few minutes before it slows to a crawl and then halts all together.  I have browsed these forums for two days straight reading everything I can about setting up a network.  I've tried the regular Network Config and the Manual config and can't seem to make anything work.  

I've tried blacklisting the old wireless driver.  I've tried to install the newest driver and ndiswrapper to no avail.  Every time I try to download them they get hung up.  I've loaded ndiswrapper to disk and it won't read the disk.

I've plugged it directly to the modem/router/wireless and nothing works.  I've tried downloading the Ubuntu updates and it gets a few in and locks up the computer completely.

I am just at a loss as what to do.  I consider myself fairly tech savvy, heck, you kinda have to be to even look into using a great linux based OS like Ubuntu and I am struggling.  I know the problem is related to the network cards because I don't have problems running open office or games or any of the other applications on the computer.  It's just whenever I connect to the internet/update that I have the issue.  

What do you all think?  Any more information that you all need?  Keep in mind that I am posting from a separate computer since I can not get onto the internet for more than two minutes with the laptop.  Thanks in advance for any help that you can give me.

---

### Post by willca on 2008-09-24
If you mean lock up as in freezing the computer all together that might not be wireless or wired network issue.

I have had that in the past and it was my HD.

I would try this, load up livecd and see if that freezes after a while.
When you load livecd, choose to have everything loaded in RAM so you can do apt-get update and all (which is where you hanging up did happen once as I read in your thread).

If this lasts longer than your usual online time on the HD install then I would run fsck against your drive.

---

