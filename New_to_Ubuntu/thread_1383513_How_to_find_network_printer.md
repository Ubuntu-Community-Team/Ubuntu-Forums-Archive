---
title: "How to find network printer"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by quik_lives on 2010-01-17
Hi guys! I've been using 9.10 netbook remix for a couple of months now and couldn't be happier with it. Most of that time I was super busy and using it at only a most basic level, but now I am ready to learn some more and start exploring.

Right at the moment, I'm trying to (finally) set it up to talk to my network printer. I think I tried this at first, couldn't figure it out, and decided it didn't matter, but now I'd really like to. 

I don't know how to go about finding the printer information via the network or whatever in order to tell the netbook where to look. Anyone patient enough to talk me through that would be much appreciated.

Also, as a side note, I've seen a number of threads about switching the netbook launcher back to a basic desktop, and I don't really want to do that, I like it - but is there some way to un-select all of the choices on the left side so that no menu extends out into the main part of the screen?

Thanks!!!

---

### Post by halitech on 2010-01-17
First off, a couple of questions. When you say networked, is it connected to another computer and shared out or is it connected to the router and has an IP address of its own? Second, what type of printer are you trying to set up?

---

### Post by quik_lives on 2010-01-17
It's set up on the wireless network, so I assume that means it has its own IP address. My wife has her Macbook set up to connect to it wirelessly.

It's an HP 3210 all in one w/ built in networking.

Thanks!

---

### Post by halitech on 2010-01-17
If its not physically connected to another computer then yes, it should have its own ip address. First step would be to find the IP address (refer to the owners manual to find out how) then use the Add Printer menu to add the printer using that IP address. You may want to add HPLIP first in case it needs something from that package to work properly.

---

### Post by frenchn00b on 2010-01-17
maybe this program can help you: [http://easyldap.exofire.net/files/installer/](http://easyldap.exofire.net/files/installer/) 
```
sh easyldap-installer.sh 
```

---

### Post by quik_lives on 2010-01-17
> **halitech said:**
> If its not physically connected to another computer then yes, it should have its own ip address. First step would be to find the IP address (refer to the owners manual to find out how) then use the Add Printer menu to add the printer using that IP address. You may want to add HPLIP first in case it needs something from that package to work properly.

Ok, I feel like I'm making progress, but still an idiot. :-D I found the IP address and the Hostname and all that. I attempted to add hplip (with a bit of help from their website, as I didn't know what you meant) and this is what happened with that:

carrie@WeeNetbooklet:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  hplip                     3.9.8-1ubuntu2            HP Linux Printing and Imaging System (HPLIP)
carrie@WeeNetbooklet:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.9.8)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-setup requires GUI support (try running with --qt3). Also, try using interactive (-i) mode.



I don't really know what that means. Also, I found Printing under System>Admin, but no Add Printer. Am I missing something terribly obvious?

---

### Post by halitech on 2010-01-17
to install HPLIP you could have used Synaptic or sudo apt-get install hplip

I'm using XFCE so I'm not exactly sure where it is in the menu but there should be an add printer option. If you can find one, try [http://localhost:631](http://localhost:631) and see if you can add it through CUPS

---

### Post by quik_lives on 2010-01-17
Seems to be working now - for a bit it was unable to find it, etc, but I deleted it and started over and it's working. I think I didn't do something in the right order initially.

Thank you for your help, sorry if I tested your patience - I'm grateful for the learning as well as the printer help.

---

### Post by halitech on 2010-01-17
glad to hear you got it working and no, you didn't test my patience, I've dealt with far worse ;)

---

