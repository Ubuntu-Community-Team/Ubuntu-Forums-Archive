---
title: "Network connected but unable to browse"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by rayfu on 2010-04-08
I have recently converted to Ubuntu  by a coworkers suggestion. My knowledge of *nix is pretty much zero. I have had no issues using an older Dell Desktop using the Desktop 9.10. Only use to surf the net, kids to do homework, check email. So far had no issues. Pretty user friendly for newbies such as myself. 

Since the desktop went smoothly created a bootable USB of NBR for my EEE PC 1000HD. Running from the flash drive I was able to get both my wired and wireless network connections to detect. I verified I obtained and IP yet when I try to browse to a website it seems to just timeout. Firefox just says connecting to "insert website name". I am not sure where or what to check. This happens when wired or wireless. Any suggestions for a serious beginner? 

If I can get this conquered I will be trying to install Ubuntu on an older Dell Inspiron e1505 which doing some research seems to have been shipped by Dell with an older version direct from Dell (7.x i believe) as a Windows alternative. 

Again I know pretty much nothing about Linux besides how to spell it.

---

### Post by undecim on 2010-04-08
Open a terminal (Applications -> Accessories -> Terminal) and copy/paste these each of these commands and post here the output of the first one that fails or gives an error.

First, network connectivity test. If your router's IP address is something other than 192.168.1.1, then you need to replace it here (your router's IP is usually the same as yours, but with a 1 as the last number)
```
ping -c 5 192.168.1.1
```

Internet Connectivity test (pings google's DNS servers):
```
ping -c 5 8.8.8.8
```

DNS Test:
```
nslookup www.google.com
```

Download test:
```
wget -O /dev/null www.google.com
```

---

### Post by rayfu on 2010-04-08
Well now I am not able to get my netbook to boot up. 

No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8.1) 

I will need to do some investigation now.

---

### Post by lidex on 2010-04-08
> **rayfu said:**
> Well now I am not able to get my netbook to boot up. 

No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8.1) 

I will need to do some investigation now.

Have seem similar issues recently, but having to do with wubi install. Is that the case here?

---

### Post by rayfu on 2010-04-08
Not sure if this is wubi related. I am not really sure exactly what that means though either. (I'm as green as a granny smith apple) I pulled the usb flash drive and tried to boot from it on a different machine and same results. I am going to format the flash drive and create it again from scratch to see if that allows me to boot up and install NBR. I am hoping I can get it to be fully functional soon so I can sell my wife on changing her OS also without too much of a fuss.

---

### Post by farsight on 2010-04-08
Hey there,

I'm by far no seasoned professional when it comes to the networks/internet etc. One thing I do suggest however, is that you ensure that the LAN and WLAN devices are enabled on your laptop. I believe when you load the system you hold F2, this resulting in the system setup (BIOS?) loading. In here you can configure which devices are switched on or off. My guess is that both are switched off at present.

I hope this helps. Good luck,
Farsight

---

### Post by rayfu on 2010-04-09
Thank you all for the suggestions. It appears that running the OS directly from the Flash drive may have caused the time out even though my network connections were enabled and connected. (This is of course an assumption on my part) 

I did resolve the mount issue by formatting the USB flash drive then creating a new clean bootable image on the that USB flash drive. I installed NBR to hard disk and behold I am now connected to the Interwebs and able to surf. (Dual boot with XP still installed) 

I'm looking forward to learning as I go. So far so good.

---

