---
title: "Can't boot after seting up WPA wireless"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by tato97 on 2007-11-15
I changed the wireless settings to create a manual Wireless connection with WPA security. Re-booted the machine. Now the system wont' boot. It hangs on the line:

* Starting Common Unix Printing System: cupsd

Several lines above it states network installation [OK] however something tells me the error has to do with the network changes. 

If I power down the system it also hangs shuting down the wireless supplicant service.

I don't remember how to list the running processed to kill the one that's hanging the system or if even that's possible. I use to work with Unix MANY moons ago...

Any help would be appreciated

Thanks

---

### Post by spd106 on 2007-11-16
Before you give up and re-install, you should try using the desktop CD's live environment to salvage the current system. If you can't boot the Ubuntu desktop CD due to memory requirements, then I would recommend you try a lightweight alternative like Damn Small Linux.

Once you've booted the live CD, you need to mount the Ubuntu partition. It should be listed in Nautilus as a storage volume and you just double-click on it to access it.

Open the /etc/network/interfaces file and comment out all lines except for the first two with the loopback interface lo. That means put a # symbol in front of each line. Once done, save and then reboot. If it says that the file is read only, then you'll have to open it as root i.e. press Alt+F2 and enter the following replacing the /path/to/ with whatever the volume is called e.g. /media/sda2/.
```
gksudo gedit /path/to/etc/network/interface
```

If you are still having trouble then you may need to blacklist a driver module. For example, I had terrible trouble with ndiswrapper one time.

---

### Post by tato97 on 2007-12-13
I posted this message about a month ago.  I'm hopping that maybe someone has found a solution to this. 

I've been waiting to install and use Ubuntu for close to two years now and everytime I install, I end up removing it because of the same issue.  My wireless doesn't work with it.  I have to admit with each new release I get closer to get it working.

Let me re-phrase, I can get it to work but I have to disable my wireless security, a risk I'm not willing to take.

I can boot the system back up it I edit the interface file and comment all the WPA entries but as soon as I re-configure WPA the system becomes unstable.  I can't open files, can't re-edit the wireless configuration and can not even power down the system.  If I force a power down, I'm back to were I started, the system won't boot up.

Several other people have commented they had the same issue.  Has anyone found a solution? 

Any help would be GREATLY appreciated.

---

