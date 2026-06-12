---
title: "Help needed with Kubuntu 8.04"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by darkrituals on 2008-04-24
Hi guys and girls,

Today i decided to add Kubuntu 8.04 to a spare notebook i have as wanted to give a linux disto a go so i now have a notebook with Kubuntu installed which i now regret as like a noob didnt think of the drivers issue so now i cannot access the net from that notebook,

Had a look around and found a tutorial on this site to setup WPN111 adapter using ndiswrapper and windows drivers for the adapter great i thought looked straight forward enough, 

so i attempted it 

opened up console and input the first piece of code from the tutorial:

sudo apt-get install build-essential

i then recvd the following message:

E: couldnt find package build essential

please could somebody help me and tell me the correct step by step way to get onto the internet after installing Kubuntu as nothing seems to work:(

sorry for the noobish question just new to linux and never had to do this sort of thing in windows.

thanks in advance

James

---

### Post by ajgreeny on 2008-04-24
I'm afraid you've suffered one of the most common problems with linux in general, not just (k)ubuntu, ie wireless networks.  If it is possible to go wired for the moment into your ethernet network port, I suspect that you will get full access to the internet.  The command you used needed the online repositories to act, so that is why you didn't get anywhere.

I have never needed nor used a wireless connection so I am not a lot of help with your particular card or the needs of that card, so others will be more use there, but the wired connection should help temporarily, at least.

---

### Post by Gaztech on 2008-04-24
You'd have thought this would have been made a little easier to deal with a la PCLinuxOS but I'm guessing 8.04 hasn't done anything about this relatively common problem :(

What you need to install is probably actually on the disk but you need to point Synpatic Package manager at the repositories on the disk. Open it up and somewhere in the settings menu you can choose where Synaptic loks for packages, point it at the CD you burnt and you should then be able to apt-get the things you need.

---

### Post by darkrituals on 2008-04-24
Hi ajgreeny,

Thanks for the reply, tried hooking the notebook up via ether to my  router but still no joy :( starting to regret changing os now lol, 

when its hooked up nothing as if its not reading the router etc, starting to think windows wasnt such as pain in the *** as i 1st thought lol,

ive even tried downloading the build essential package on this pc and then putting it on a usb and transfering the file but when i click the DEB file it springs a not satisfied error :(

surely there must be a way of accessing the net from a fresh install as the wirless card, router will not be recognised once Kubuntu is installed and the only way to get them recognised is to use the build essential command and ndiswrapper which u cant  use due to build_essential not been included in the OS install.

James

---

### Post by Ayuthia on 2008-04-24
> **darkrituals said:**
> Hi ajgreeny,

Thanks for the reply, tried hooking the notebook up via ether to my  router but still no joy :( starting to regret changing os now lol, 

when its hooked up nothing as if its not reading the router etc, starting to think windows wasnt such as pain in the *** as i 1st thought lol,

ive even tried downloading the build essential package on this pc and then putting it on a usb and transfering the file but when i click the DEB file it springs a not satisfied error :(

surely there must be a way of accessing the net from a fresh install as the wirless card, router will not be recognised once Kubuntu is installed and the only way to get them recognised is to use the build essential command and ndiswrapper which u cant  use due to build_essential not been included in the OS install.

James

Ndiswrapper should be on the install CD.  All you need to do is put in the 8.04 CD and install ndiswrapper-common and ndiswrapper-utils-1.9

---

