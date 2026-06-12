---
title: "Home network printer problems"
date: 2014-10-17
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2014-10-17
Evening, all. 

I've got a little problem here..!

My main workhorse is running Ubuntu 14.04 ( and also Kubuntu, Xubuntu, Lubuntu.....but I digress.) The other machine in the household belongs to Mum, whom I look after. It WAS running just Windows 7, but it's now dual-booting with Ubuntu 14.04; a very smooth installation, too.

I've decided to try and set up network printing. I have an Epson SX218, connected to my machine by USB.....and my Compaq Presario desktop is connected to our home router (a British Telecom Home Hub 5) by Ethernet. Mum's computer is connected to the router by wireless, naturally; it's a Dell N5110 Inspiron laptop.....known by some as a 15R.

When the Dell is running Ubuntu, it prints to my printer as sweet as a nut, having enabled sharing on both systems, and 'Publish shared printers connected to this system'. I've installed SAMBA, and have the printer set not only as a local printer, but also as a remote printer for other machines.....because I want to be able to print from Windows 7 (vis-a-vis this wiki):-

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

It makes no difference to Ubuntu on Mum's machine whether I use the 'shared' option or the remote printer option; it still prints perfectly. The problem, at the moment, seems to be that Windows just isn't 'seeing' my computer on the network AT ALL.....let alone being able to 'see', and connect to, the printer.

I've spent that long on the net trying to figure this out this afternoon I'm developing square eyes..! :p I know Windows can be pain in the unmentionables at the BEST of times....but I didn't think it was going to be THIS awkward..!

Can anybody with a wee bit more experience in this area advise me as what I'm doing wrong? ANY advice would be appreciated.

Regards,

Mike.

---

### Post by westie457 on 2014-10-17
Evening Mike_Walsh

Is the problem mainly that you have no networking capabilities at all from the Windows machines? Or just that you cannot set up a networked printer?
For the printer, in Windows give this link a try. It is for a different printer however the procedure should be the same. [http://www.sevenforums.com/network-sharing/243783-can-t-install-network-printer.html](http://www.sevenforums.com/network-sharing/243783-can-t-install-network-printer.html)
Other than that my networking set up knowledge is very limited. Managed it once 3 years ago and then had to re-install everything after I messed up something else.

Let us know how it goes.

---

### Post by Mike_Walsh on 2014-10-17
Hi, westie!

Thanks for the reply. I'm probably in the same boat as you. I've been playing around with these things for more years than I care to remember, but I've never tried networking before.....and the first time I decide to try this is in Linux..!

I'm really very impressed with just how easy it is to set up network printing in Ubuntu; but Windows 7 is being a bit of a pig, to put it mildly; hardly unexpected, really. It's just that since it's Mum's machine, not mine, I WOULD like to try and get it working in BOTH OSs; I promised her I would, and I don't renege on my promises...

I'll have a look at that link, and let you know how I get on. Appreciated. Probably won't get back to you till tomorrow afternoon at the earliest, I'm afraid; family coming over for a visit!

Regards,

Mike.:)

---

### Post by weatherman2 on 2014-10-17
Have you tried searching in Windows 7 by IP address for your printer?  I mean, whatever the IP is of your Ubuntu machine that is connected to the printer via USB.

You might also choose "printer on the internet" as an option in Windows and use "[COLOR=#333333][FONT=UbuntuRegular]http://{computername}:631/printers/{printername}" as the URL of the printer.  I know I did this a few times in the past but not recently...[/FONT][/COLOR]

---

### Post by Mike_Walsh on 2014-10-17
Hey, weatherman.

At the moment, I'm open to ANY suggestions! I've followed the link in westie's post above, and I THINK (I think) I've managed to add it. That link led me onto something else (as they usually do!), and THAT had the suggestion to use the IP address of the computer you want to connect to. It probably helped that I'd already installed the drivers for this printer on Mum's computer some time ago.

At any rate, it got to the stage where it asked me if I wanted to print a test page, so..... I shall try it in the morning; I'm too knackered tonight to bother with it!

Quite WHY Windows wants to install the driver for the printer when it's already connected to ANOTHER computer, using a totally different driver, configured for THAT machine, I don't understand. I'm very new to this whole business of networking, despite having used these things for  over 30 years; I've simply never had the need before. It's now getting under my skin.....and I've never let anything beat me yet!

That's what I love about forums in general, and this one in particular; the vast number of folk who are only too happy to share their knowledge & help one another out...

WhatEVER did we all do before the rise of t'internet? \\:D/

Regards,

Mike.

---

### Post by Vladlenin5000 on 2014-10-17
Each OS / each machine in the network **needs **its own compatible driver. 
Connecting locally or remotely, as far as the OS is concerned doesn't matter. The machine acting as the print server must have those drivers already otherwise you wouldn't even be able to share it to the network. Any other machine will install and/or try to use the best driver it has available.

You best bet is always installing the drivers in the remote PC from where you want to print to the network printer before attempting to configure that new network printer. Some Windows installers of some printers (Epson, HP, etc.) even allow you to select local or network at some point. Selecting network will then trigger the drivers installer to browse the network in search of a compatible printer and they usually find it and all it's needed is done for you by that installer.

---

### Post by Mike_Walsh on 2014-10-18
> **Vladlenin5000 said:**
> Each OS / each machine in the network **needs **its own compatible driver. 
Connecting locally or remotely, as far as the OS is concerned doesn't matter. The machine acting as the print server must have those drivers already otherwise you wouldn't even be able to share it to the network. Any other machine will install and/or try to use the best driver it has available.

You best bet is always installing the drivers in the remote PC from where you want to print to the network printer before attempting to configure that new network printer. Some Windows installers of some printers (Epson, HP, etc.) even allow you to select local or network at some point. Selecting network will then trigger the drivers installer to browse the network in search of a compatible printer and they usually find it and all it's needed is done for you by that installer.

Thanks for that, Vlad.

That's made things a bit clearer! In fact, it explains why, when I finally got the network printer to install, it went so smoothly.....because I'd already installed the Epson driver to the machine some time previously.

Yet another nugget of information to remember! Much appreciated.

Regards,

Mike.

---

### Post by Vladlenin5000 on 2014-10-18
You're welcome :p

---

