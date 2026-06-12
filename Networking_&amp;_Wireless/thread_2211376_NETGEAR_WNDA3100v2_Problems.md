---
title: "NETGEAR WNDA3100v2 Problems"
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by Jordan_Avery on 2014-03-15
Okay, so there are a thousand things online about getting the NETGEAR WNDA3100v2 to work with Linux (I'm running Ubuntu 12.04 LTS with latest updates).
Over the last 24 hours I have literally tried every possible thing they listed, so I decided I would ask on my own thread and see if we can get this to work.

One big note to all who view this page, I have NO internet access for this computer so I can't download anything (unless you can teach me how to be smart and burn programs to a disc from a different computer so that they work :P)

Here's the run down on what I did do:
- I have installed WINE. I tried to download it on a laptop, burn to disc, and run it on the computer in question but no go. 
      I had to use the last bit of data on my wife's phone via tethering in order to download.
- I've installed from the WNDA3100v2 and the genie is on my desktop, but it won't open with WINE.
- The computer says the driver was installed successfully, but it is not working. I do have the driver file.
- The USB device appears with lsusb in the Terminal as "Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Brandcom BCM4323]

Obviously, this isn't for Ubuntu 12.04 LTS but I tried all the steps in this post [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708) and still had no luck.

If you people-who-are-much-wiser-than-me have any suggestions, please share them. I'm about ready to pull my hair out.

Cheers

---

### Post by chili555 on 2014-03-15
I know I will hate myself in the morning since I am about to stick my hand into the hornet's nest. Please check here: [http://ubuntuforums.org/showthread.php?t=1975638](http://ubuntuforums.org/showthread.php?t=1975638) I've attached the files you need. Be sure to install either the 32- or 64-bit files; find which you need with the terminal command:```
arch
```It is tricky and may not work. > unless you can teach me how to be smart and burn programs to a disc from a different computer so that they workPretty easy, actually. A USB is much easier, however.

---

### Post by Jordan_Avery on 2014-03-17
Thanks for responding! I will give it a go in the morning.

And if you could provide instructions for the USB, that would be awesome. 

Cheers

---

### Post by chili555 on 2014-03-17
> **Jordan_Avery said:**
> Thanks for responding! I will give it a go in the morning.

And if you could provide instructions for the USB, that would be awesome. 

CheersSure. Dowload the packages you need on any other computer. Stick the USB in and drag and drop the files to the USB. Safely remove the USB and stick it in the Ubuntu computer. Drag and drop them to the desktop. You should then be able to right-click them and select 'Open with Software Center.' If you are old-school like me (read: just plain old), open a terminal and do:```
cd ~/Desktop
sudo dpkg -i <some_package>*.deb
```The wildcard * is so you don't need to carefully type out liblightdm-gobject-1-0_1.8.5-0ubuntu1_amd64.deb; you can just type, in my example, liblightdm*.deb.

---

### Post by Jordan_Avery on 2014-03-17
I'm giving it all a try, I'll let you know the results :)

---

### Post by Jordan_Avery on 2014-03-17
Okay so I'm stuck.
I downloaded the attachment from that other forum, and did the arch command which confirmed I have 32-bit which I all ready knew. 
The problem I'm having it I can't get ndiswrapper to work. I have the tar.gz file on my desktop and when I open it and click on INSTALL it just brings up a note pad of what to do.

It says I need to get a kernel higher than 2.6.13, and "Make sure there is a link to the kernel source from the modules directory. The command

ls /lib/modules/'uname -r' /build

should have at least 'include' directory and '.config' file." What is that supposed to mean?

Next it tells me to download the lastest version, which I have and now it says to extract it with the command 

"tar zxvf ndiswrapper-version.tar.gz"
 
I have version 1.59, so what I entered is "tar zxvf ndiswrapper-1.59.tar.gz"

The response in the terminal was:
tar (child): ndiswrapper-1.59.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

So, I'm stumped. Any help would be awesome. :)

---

### Post by chili555 on 2014-03-17
> Make sure there is a link to the kernel source from the modules directory.That, in Ubuntu-speak, simply means to install linux-headers matching your running kernel. Did you? How aboult build-essential? > The computer says the driver was installed successfullyPlease show me:```
ndiswrapper -l
```

---

### Post by Jordan_Avery on 2014-03-17
The actual program said it installed correctly without ndiswrapper, but I'll enter that into the terminal.

Also, if my kernel isn't matching the headers, I would need to know how to do that and build essential. I'm extremely new to Ubuntu, as you can tell.

Okay, it gave me a whole bunch of stuff to type. Just a moment.

---

### Post by Jordan_Avery on 2014-03-17
username@computer: ndiswrapper -l
The program 'ndiswrapper' is currently not installed. You can install it by typing:
sudo apt-get install ndiswrapper-common
username@computer: sudo apt-get install ndiswrapper-common
[sudo] password for username:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
    ndiswrapper-source
The following NEW packages will be installed:
    ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 653 not upgraded. (need the internet first :/ )
Need to get 5,988 B of archives.
After this opperation, 72.7 kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main ndiswrapper-common all 1.57-1ubuntu1
    Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.57-1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.57-1ubuntu1_all.deb) Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

End script.

---

### Post by chili555 on 2014-03-17
Pardon me. I made a mistake. My mistake was answering the question, 'how do I do this' by telling you how to do what you asked. That was a mistake. I should have said that you don't really want or need to do what you are asking; you need to do something else. Sorry.

You don't want or need to compile ndiswrapper from a tar.gz. It is complex and difficult and I am too old to wait that long. What you really want to do is give that Netgear to a Windows friend and kiss it goodbye. Do a bit of research here and find a US$10-15 USB device that works the moment you plug it in.

If you are unwilling to do that and insist on trying to get this pig to fly, get ndiswrapper and its dependencies here: [http://packages.ubuntu.com/precise/ndiswrapper-common](http://packages.ubuntu.com/precise/ndiswrapper-common) and here: [http://packages.ubuntu.com/precise/ndiswrapper-utils-1.9](http://packages.ubuntu.com/precise/ndiswrapper-utils-1.9) Dependencies are those packages on each page marked with a red dot. It appears that you only need libc6. It may already be installed; check:```
sudo dpkg -s libc6
```If it reports Status: install ok installed, then you just need the two packages. If not, add it to the list of things that need to be downloaded and installed as above.

---

### Post by Jordan_Avery on 2014-03-17
Yeah I knew this was going to be a bigger pain in the butt than it is worth, but I wanted to give it a go. I read that the adapter I have is the hardest one to get to work with Linux.
I do have libc6 so if I continue to walk down this path I just need ndiswrapper and the dependencies. I apologize if this has given you a headache, cause I know it definitely has given me a constant one for a week. I really do appreciate your help with my goal. I found a $16 adapter that is optimized for linux, so I will probably just go ahead and order that if I can't get this to work. The problem isn't that I can't get any other adapter, it's the fact that I'm working on this computer so my brother in law can have something that functions while I fix his computer. I'm a Windows and Mac guy, and I do like Ubuntu it is just a little too complex for me. By getting the adapter working, the computer would be in working order before he comes to pick it up but hopefully, Amazon can deliver before then haha.

Again, thank you for your time. I appreciate it

---

### Post by chili555 on 2014-03-17
Get the two ndiswrapper packages, install them as above and let's keep going forward.

This device has been a pain in my butt for 3-4 years, actually and I don't even own one!

---

