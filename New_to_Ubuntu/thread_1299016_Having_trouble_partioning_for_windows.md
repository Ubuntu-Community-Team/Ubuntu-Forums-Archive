---
title: "Having trouble partioning for windows?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by b.mulqueen on 2009-10-23
Hey guys. I am at the point of pulling my hair out. Here is the long version. I am running a ubuntu 9.04 solely.

Being I want to start making music on the computer(ableton live, vst's and such). So I was hoping at first to do it running a virtual machine with ubuntu as host to windows. That didnt work out.

So I said to myself, let me partition my main hdd with gpartition to run dual boot. 
That isn't working.

I've been googling for a couple of days now, I am am figuring let me ask from the getko what I should do.

So let me mention my situation. I like ubuntu. I want to use it for anything I wont need windows for ex. music daw's and drafting.
I dont want to use windows for anything internet related.
I have burned a copy of Ubuntu 9.04 live cd.
I have a copy of windows xp pro and serial.
I need the windows drivers for my computer, i think i have found them here 

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=402165&prodTypeId=12454&prodSeriesId=402163&swEnvOID=1093&taskId=135&swLang=13](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=402165&prodTypeId=12454&prodSeriesId=402163&swEnvOID=1093&taskId=135&swLang=13)

I have a 30gb internal hdd. and a 1tb external hdd.

Hopefully some one can give me some advice(what you think my best options would be in this situation) or point me in the right direction.

Sorry if this is long winded, or has been asked a million time, I just find myself running in circles here.

Sorry if this in the wrong forum.

---

### Post by undecim on 2009-10-23
Well, first off, you need to be running gparted from a livecd to mess with partitions

A warning though: Windows will nerf you grub installation. There is a help article written on fixing this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I would recommend instead trying the virtual machine option again, especially if you have a recent CPU which supports hardware virtualization. It saves the trouble of restarting, and makes it easier to share files between the two. (just make sure you change the network adapter type to "Internal Network" since you don't want XP connected to the itnernet)

I can help with that if you need; Just post any problems you have here

If that doesn't work, there is also WINE, which you can install from the directions athttp://winehq.org/ and see if that will run whatever windows applications you need. sure

---

### Post by kansasnoob on 2009-10-23
See if this helps:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by b.mulqueen on 2009-10-23
Thank you. I have tried to install vmware and virtual box to no avail.

Which would you recommend. And would you help me out step by step. Or point me to the best guide, I've tried a couple already.

---

