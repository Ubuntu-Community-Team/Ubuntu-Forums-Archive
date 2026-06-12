---
title: "No wlan0"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by moonscapex on 2009-07-15
Hi,
I am trying to configure Angstrom Linux wifi.  The documentation is really bad and half of it I cannot understand.  I followed the instructions at [http://linuxtogo.org/gowiki/AngstromManual](http://linuxtogo.org/gowiki/AngstromManual) (the part that says Networking using wifi/802.11).  After I try to follow the steps, I get this error when bringing up wlan0 ([FONT="Courier New"]ifup wlan0[/FONT]):

[FONT="Fixedsys"]Set failed on device wlan0 ; No such device.[/FONT]

Can someone help me or give me easier instructions.
Thanks,
Will

---

### Post by moonscapex on 2009-07-15
Some more details:
I am running an HP Ipaq h4000 series and entering the commands in a root shell.
I have not rebooted the handheld yet.

---

### Post by kilowattradio on 2009-07-15
> **moonscapex said:**
> Hi,
I am trying to configure Angstrom Linux wifi.  The documentation is really bad and half of it I cannot understand.  I followed the instructions at [http://linuxtogo.org/gowiki/AngstromManual](http://linuxtogo.org/gowiki/AngstromManual) (the part that says Networking using wifi/802.11).  After I try to follow the steps, I get this error when bringing up wlan0 ([FONT="Courier New"]ifup wlan0[/FONT]):

[FONT="Fixedsys"]Set failed on device wlan0 ; No such device.[/FONT]

Can someone help me or give me easier instructions.
Thanks,
Will
 You need to have the driver also called module be used on start up of the network wireless card or booting of the computer. The problem is that does the kernel in Ubuntu support that module and does the provided driver/module work with the wireless card. See if Ubuntu has a compatibilty list of products that will work with your wireless card. If they don't support your card you will have to see if ther is a driver/module that WORKS with your card. Then you will have to compile it and install it. What I did for a card that worked with linux is find one that worked and bought a used one of eBay for five bucks +shipping. It took a week, but I didn't have to create my own module for the item. If you can't replace the wireless card in your computer, look for a compatible USB wireless card that works in Linux Ubuntu. 
 I hope some of these ideas and options are helpful. 

Keith

---

### Post by moonscapex on 2009-07-15
Thanks for the ideas, but I am not running Ubuntu.
I am using _Angstrom_ linux, with only a command line.

---

### Post by moonscapex on 2009-07-15
I think I will put Windows mobile back on.  It looks like it's going to be to hard.  Even USB networking doesn't work.

---

### Post by Hospadar on 2009-07-15
Your network interface might not be called wlan0.
The wifi on my laptop is eth1

Your card might be supported just fine and only in need of a little configuration.

Could you post the output of a couple commands:

iwconfig

ifconfig

lshw -C network

---

