---
title: "iOS 4.3 for iPhone 4/VirtualBox anybody?"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by DavidMorton on 2011-03-10
I'm curious to know if anybody has successfully upgraded to iOS 4.3 and has synced using a Windows VM in VirtualBox.  I'm just checking before I do my upgrade and hose myself if it doesn't work.

---

### Post by neyanderson on 2011-03-10
I got the same problem using VMware.

---

### Post by DavidMorton on 2011-03-10
Oh, there wasn't a problem at all.  In fact, I went ahead and took the plunge.  It worked fine.  I updated to iOS 4.3 using a VirtualBox running Windows 7 32-bit, while running the host as 10.10 32-bit.  I had to occasionally "reattach" the iDevice to the guest, as VirtualBox wasn't doing it for me, but it works now.  It synced fine.

---

### Post by Heiner on 2011-03-11
I am running Kubuntu 10.10 x64 with Windows 7 (x64) in VirtualBox 4.04. There I installed the latest iTunes to update my iPad from iOS 4.2 to iOS 4.3. First, it seemed to work. iPad was connected and update started. Then I went to bed and in the next morning I got an error message saying that the update failed (I cannot remember exactly). The iPad was identified as "Apple Mobile Device (Recovery Mode)" and I was not able to connect it to the virtual machine (it was greyed out). The solution to this problem was to add my user account to the group "vboxusers". After a restart, I was able to connect my iPad to the virtual machine and iTunes detected it and the update was completed. Now, everything works fine.

---

### Post by falsedichotomies on 2011-03-11
I was able to successfully update my 3G iPod Touch in a 32 bit XP Pro VM by creating a USB filter for it and keeping my mouse hovered over the USB Devices menu in VirtualBox for the entirety of the process (don't know why, but it works).

I kind of wish that I hadn't upgraded though, because the iPod, although mounting, is no longer syncing back in Ubuntu, and I have to boot up my horribly slow VM and the terrible iTunes to put music on it now. Anyone else experiencing syncing problems back in Ubuntu?

---

### Post by patrickballeux on 2011-03-17
> **falsedichotomies said:**
> I was able to successfully update my 3G iPod Touch in a 32 bit XP Pro VM by creating a USB filter for it and keeping my mouse hovered over the USB Devices menu in VirtualBox for the entirety of the process (don't know why, but it works).

I kind of wish that I hadn't upgraded though, because the iPod, although mounting, is no longer syncing back in Ubuntu, and I have to boot up my horribly slow VM and the terrible iTunes to put music on it now. Anyone else experiencing syncing problems back in Ubuntu?

Same here, with iOS 4.3, I cannot put any mp3/movies on my devices (iphone/ipad).  

Look at Fusion Stream in the app stop.  If you have MediaTomb setup than you can use them to transfer over wifi.  You won't be able to use the iPod app, but Fusion Stream does a good job also.

I am currently using the PPA for iPhone's libs but still no luck as of today.

---

### Post by dmartin on 2011-03-18
Heiner's tip about adding yourself to "vboxusers" is excellent.  All devices stop being "greyed out" when you are in that group.  

For the record, this change doesn't require a reboot, just a log out and log back in to set the env variables into the current session.  You could even avoid logging out if you ran virtualbox from a new terminal window.

---

### Post by XProgrammer on 2011-03-20
@Heiner

Thanks alot. 

My user name was part of vboxusers group. However, I wasn't caring much about it. So added it again and restarted the Ubuntu. Now, VM is detected my iPad recovery mode. 

It works.

---

### Post by dbwhitaker on 2011-03-27
It's not working well for me at all. Things had been working fine for me until I tried to upgrade from iOS 4.2 to 4.3. The update failed due to USB problems, so I used a "real" Windows PC to complete the upgrade. Now that I'm connecting again to my VirtualBox VM (Windows XP guest, Ubuntu 10.10 host, VirtualBox 4.0.4) I can only sync settings and a couple of apps. Syns for the majority of apps is failing due to USB timeouts. iTunes is generally unresponsive during sync, and takes several hours to complete the sync operation even though the result is that about 30 apps have failed to sync (i.e. load) on to my iPhone. It's unfortunate that I can't modify device sync settings in iTunes except when the device is connected (because as soon as it connects it tries to sync, and immediately becomes unresponsive).

---

### Post by pwizzle14 on 2011-04-18
i have a question? when i try to mount my iPhone (which i just got) into ubuntu it says unable to mount, but if i use virtual box with windows 7 i get a MTP error with windows looks for the driver? i also did the idevicepair unpair etc stuff already to. aslo in ubuntu, rhythm box bout see my iphone but is unable to sync the songs thanks for the help

---

### Post by pwizzle14 on 2011-04-18
I got it working... had the

 MDP error follow
[http://support.apple.com/kb/ts1538](http://support.apple.com/kb/ts1538)

then when u get the apple mobile device driver loaded go to virtualbox's website and download the USB extension pack. That should do the trick. well it did for me.

---

