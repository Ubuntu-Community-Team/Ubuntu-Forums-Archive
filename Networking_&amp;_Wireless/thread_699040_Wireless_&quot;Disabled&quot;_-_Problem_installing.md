---
title: "Wireless &quot;Disabled&quot; - Problem installing Ndiswrapper"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by taz5005 on 2008-02-17
I'm having some problems getting my wireless to work on my laptop.  I've got an Acer Aspire 3680 with a Broadcom BCM94311MCG wlan card. 

Firstly, when I check 

lshw -C network  

I get it saying my wireless interface "*-network DISABLED"

So I'm trying to install ndiswrapper and I've been following How To: Install Ndiswrapper ([http://ubuntuforums.org/showthread.php?t=574501&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=install+ndiswrapper))
and it was going fairly well until I had to edit the /etc/iftab file to change the logical name from eth1 to wlan0.

I don't have the file...???

I don't know where to go from here...and it still says the network is disabled...I don't know if that's ok or if it should be changed by this point.

This is really getting me down...I just bought the laptop and I really need to be able to get online!

btw, I do NOT have wired access to the net, but I do have another computer that I can transfer files to/from.

---

### Post by Hightide on 2008-02-17
HI Taz5005

This [thread]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/") may point you in the right direction


regards


:)

---

### Post by taz5005 on 2008-02-17
I've seen that, but it assumes you have an internet connection.  I'll be goin home later tonight so I'll try to get it done there (where I have a wired internet connection).  I'll let you know about my results.

---

### Post by Paul86fxr on 2008-02-17
taz, send me an address and I will send you a zip file with ndsiwrapper, offline mode as well as online mode, it should get you up and running.

Paul
[email]Paul49203@yahoo.com[/email]

---

### Post by taz5005 on 2008-02-19
Solved!!  The offline installer for the program worked great; at first it said the installer isn't supported for Gutsy, but I tried the offline one anyways (it gives options for online or offline) and it worked.  Thanks everyone!

---

