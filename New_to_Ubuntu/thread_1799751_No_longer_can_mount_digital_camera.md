---
title: "No longer can mount digital camera"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by k33bz on 2011-07-08
Just a week ago I was able to plug my camera (FujiFilm FinePix F480) and it would mount automatically. However today I tried to mount it, and it refuses to mount. I have looked high and low for a way to get it to mount, including sudo modprobe usb_storage and sudo modprobe -r floppy. I have rebooted and still does not mount. I have tried usbmount, nothing seems to work.

sudo ls -l /dev/disk/by-id/*usb* shows nothing
sudo fdisk -l does not see it

dmesg
```
[ 3075.384100] usb 1-2: new high speed USB device using ehci_hcd and address 9
[ 3075.518104] usb 1-2: configuration #1 chosen from 1 choice

```
This does not loop over and over like I have seen others do.

lsusb shows the camera.

Although I am able to get the pictures from the camera through camera.app with gnustep. But this does not let me choose which pictures to take off, just all or none. Which is why I want to be able to view them when mounted.

---

### Post by nomko on 2011-07-08
I have a Canon 450D camera and i always remove the memory card and put it in a cardreader. That works fine for me! Did you try this?

---

### Post by k33bz on 2011-07-08
My laptop wont accept the card that the camera uses :( so unfortunately this is not an option for me.

BTW GtKam also pulls up the pictures, but does not let me save them or delete them.

---

### Post by k33bz on 2011-07-08
*bump*

---

### Post by no2498 on 2011-07-08
try taking the card out plug the cam in  then put the card in
it may work

---

### Post by k33bz on 2011-07-08
> **no2498 said:**
> try taking the card out plug the cam in  then put the card in
it may work

Went to try that, however, the battery and card are in same place, thus keeping the cover open or opening it period makes the camera inoperable since the electric current is broken. :(

---

### Post by dFlyer on 2011-07-08
Have you recently changed any of your settings, like choosing Do Nothing when your camera is mounted.

---

### Post by k33bz on 2011-07-08
> **dFlyer said:**
> Have you recently changed any of your settings, like choosing Do Nothing when your camera is mounted.

Only thing I have done is install a few updates, one of which is a new kernel. The only other thing I have done was remove pulseaudio and reinstall esound due to me wanting to use my mic in secondlife. Because of installing esound I lost keyboard hotkeys for adjusting volume, so I installed the glade packages and a different set of gnome-sound-properties, tut found here [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973/comments/11]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973/comments/11").

However to test if these two things were it, first I ran my laptop in a previous kernel, and I have also named the glade file with a .bak file extension, as well as with the gnome-sound-properties.bak. Neither of these has gotten my camera mounting back.

---

### Post by k33bz on 2011-07-09
*Bump*

---

### Post by Wim Sturkenboom on 2011-07-09
Check if you have not changed any settings on the camera with regards to the USB port (e.g. used the camera to print directly on a printer).

---

### Post by k33bz on 2011-07-09
> **Wim Sturkenboom said:**
> Check if you have not changed any settings on the camera with regards to the USB port (e.g. used the camera to print directly on a printer).

Even if I wanted to, I am not able to change those kind of settings on the camera, they are hard printed into the software. Whats funny is my wife runs 10.04 as well branched out from the ubuntu studio distro, and it still mounts the camera. Wondering why mine wont is what is bugging me.

---

### Post by wep940 on 2011-07-09
I think what may be going on is a change in the udev rules for mounting USB devices. This would result in the symptoms you describe, as the device would be owned by root and you would not be able to access it.
 
Please post back the output of your lsusb while the device is plugged in as we need the manufacturer id and product id for your camera from that. Also the version of Ubuntu or its derivative you are running.
 
EDIT:  You are saying the camera isn't visible under "Places" as well, correct?  Try sudo nautilus and see if it is visible then.

---

### Post by k33bz on 2011-07-09
> **wep940 said:**
> I think what may be going on is a change in the udev rules for mounting USB devices. This would result in the symptoms you describe, as the device would be owned by root and you would not be able to access it.
 
Please post back the output of your lsusb while the device is plugged in as we need the manufacturer id and product id for your camera from that. Also the version of Ubuntu or its derivative you are running.
 
EDIT:  You are saying the camera isn't visible under "Places" as well, correct?  Try sudo nautilus and see if it is visible then.

lsusb
```
Bus 001 Device 004: ID 04cb:01dc Fuji Photo Film Co., Ltd 

```

still cant see it under sudo nautilus either. Wouldnt the udev rules apply to all usb storage devices, my flash drives still mount as before, it is just the camera that doesnt.

---

### Post by wep940 on 2011-07-09
> **k33bz said:**
> lsusb
```
Bus 001 Device 004: ID 04cb:01dc Fuji Photo Film Co., Ltd 

```still cant see it under sudo nautilus either. Wouldnt the udev rules apply to all usb storage devices, my flash drives still mount as before, it is just the camera that doesnt.

The udev rules work quite strange at times.  I know that if it's an unknow usb device that it only gives access to root.  However, since your sudo nautilus still doesn't show it. I need to look around a little yet.

---

### Post by k33bz on 2011-07-09
k, thank you

---

### Post by k33bz on 2011-07-12
*bump*

---

### Post by wep940 on 2011-07-12
Sorry I haven't gotten back to you yet.  I'm still looking for a solution.  In the mean time, I'll try to post back to you sometime tomorrow a udev rule file to try to see if it helps any.

---

### Post by k33bz on 2011-07-13
> **wep940 said:**
> Sorry I haven't gotten back to you yet.  I'm still looking for a solution.  In the mean time, I'll try to post back to you sometime tomorrow a udev rule file to try to see if it helps any.

Well a little update, I went ahead and upgraded to 10.10. Some of the stuff that went wrong got fixed, however still not able to mount camera. If you cant find a solution, it is no big deal, I may just install Debian instead. Sad to say, cause until recently I have been very happy with Ubuntu, been with Ubuntu since Dapper. The new changes that have been made with 11.04 and the ones coming with 11.10 I am not happy at all with.

---

