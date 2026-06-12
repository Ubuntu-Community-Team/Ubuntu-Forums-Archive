---
title: "Gutsy wired connection only works if roaming is chosen"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2007-10-23
Upgraded to Gutsy yesterday but my wired connection from PC to wireless router only works if roaming is enabled  in Network Manager (the default?)  but not if I select DHCP. I'm not sure how this will all work out when two other family members are using their PCs to connect using wireless to the router. This happens also with my 64 bit Gutsy OS on my other HDrive.

Co-incidentally perhaps, I might have recently physically disturbed my mobo's  Lan socket and today  I've only managed to connect by using a separate Lan card.

Do you have to enable roaming to connect with a wired link and what about DHCP? Interesting concept though to enable wired roaming, sounds a bit like using a dog lead.

---

### Post by spd106 on 2007-10-23
Roaming mode allows Network Manager to turn interfaces on or off depending on what's available. So it will automatically switch to the wireless card if you unplug and back to wired when you plug back in again.

So as roaming mode uses DHCP anyway, there's little to be gained in turning it off. Unless you connect to two different networks, but that can cause routing conflicts if you have multiple default gateways.

I am unable to reproduce your problem, have you tried un-ticking and then re-ticking the box next to the interface? There should be a pop-up changing state progress bar, if not trying opening a terminal and running these commands (assuming your interface is called eth0).

```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by Handssolow on 2007-10-23
Thanks for your reply spd 106. I removed my RT2500 based Wlan card several weeks ago because it didn't work well for me with Feisty and I also had concerns about wireless security. After reading your posting I  removed my pci Lan card, enabled the on-board Lan in the bios and initially couldn't get a network connection. The on-board lan is what I've been using with Feisty.
I'm still not sure if I have a faulty network socket on the mobo anyway here's the latest-
On booting initially up there was no network connection using the on-board lan
sudo ifdown eth0
sudo ifup eth0
initially reported eth0 wasn't configured

I also saw an error message about Firestarter in the terminal-
/etc/network/if-up.d/50firstarter exited with return code 2

Looking at Firstarter Application I had no network connection

I then tried switching between  selecting roaming or DHCP and repeating downing and upping eth0 plus one wiggle of the cable in the network socket. The next moment I've got a network connection again.
It's working, roaming box isn't selected and I'm on DHCP but strangely right clicking the top tool bar over the network icon shows a tick by "Enable  Networking" but "Connection information" is pale grey usually indicative of no connection.

I'll see tomorrow if this problem returns.

---

### Post by Handssolow on 2007-10-24
If I select roaming I get an internet connection when I reboot, the top toolbar show  "Wired Network connection" and  when I place the mouse pointer over the monitors icon  I can right click to obtain Connection information. So far so good perhaps. Incidentally I've removed Firestarter.

What I hadn't mentioned before was since upgrading to Gutsy every time I open  Evolution Mail a box opens indicating that it cannot connect and requests I enter my password though the black dots indicate that my password has been remembered. However, if I close the box I've just discovered I can send and receive emails anyway.

Any suggestions

---

### Post by Scareface on 2007-10-24
Hi.
I have got the same problem. I can only browse internet pages using Firefox. If I try to check emails in Evolution or login in pidgin, I can't. And I can't also to update the software sources. It write me connection timed out. It is the same by you?
Thanks 

Scareface

---

### Post by Handssolow on 2007-10-24
Hi Scaface, I'm sorry to read of your problems with updates and Evolution Mail it sounds like you've got more than one issue to sort out. Here are my humble suggestions.

With your updates, have you tried using the terminal to update?
sudo apt-get update
sudo apt-get upgrade

My upgrade sent me back to linux-386 rather than linux-generic which I need so I can use both my Athlon dual cpus so I had to modify
sudo gedit /boot/grub/menu.lst 
to block 386 being loaded at boot and instead I choose generic. I had also to reconfigure xserver with sudo dpkg-reconfigure xserver-xorg

I also have an issue because I'm using an Nvidia based video card and use a Restricted Driver. Sometimes I check updates with
sudo apt-get install linux-generic

sudo apt-get install linux-386 if you have single based cpu system.

With Evolution Mail it appears with me that somethings have been changed during  my upgrade from Feisty to Gutsy. Now I get a notifiication that I've got new mail on the top tool bar which seems unnecessary considering that I can already see I've new mail. Plus the appearance of a dialogue box asking me to input my POP password every time I open Evolution Mail.

---

### Post by Handssolow on 2007-10-28
Just an update.
Having looked in my Administration>System Log I wasn't happy having roaming selected with my wired connection as it appeared to be throwing up some errors, so in System>Network I've deselected roaming, selected DHCP and ticked the box for wired. I did have to input a few of sudo ifdown eth0 and sudo ifup eth0 before I got connected to my wireless router. It seems now to be working with fewer log errors. Though it  looks like a file is still is looking for my wireless card  which I removed a few weeks ago.

---

