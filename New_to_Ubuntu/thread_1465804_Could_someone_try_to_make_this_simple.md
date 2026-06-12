---
title: "Could someone try to make this simple?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-04-29
Im trying to install drivers for a network usb card. 
on the instructions it says, 
For starters,

Please check which driver you should use:
	1. Insert ASUS 167g into USB port.
	2. **cat /proc/usb/devices. **
	3. Check vendor id and product id of ASUS WLAN device.
	4. Follow the README file in related directory to compile and install driver.
	
Where do i find the part that is in bold?, i couldn't find it anywhere :/

Im sorry but i can't paste the read me file in the download since i have no internet on my linux machine, i can't open the files on windows to get them ether. If someone would like to download this and paste it in this thread it would be great (:
Its the part that asks me to build the file. Also when it asks about kernel. Im not quite sure what i am ment to put :/. 
Oh im using 10.04 beta. some problems with my laptop not burning disks properly i haven't updated to the real version. I would like to install it on this first so i know how to do it anyways.

---

### Post by wojox on 2010-04-29
You enter the part in bold into the terminal and it will show you the the file.

---

### Post by Rave Gloves on 2010-04-29
Im not sure if it's my device that's faulty or not. it is second hand. when i plug it into the usb it flashes as it goes in then nothing. Im getting a "no such file found " error when i try to search for the folder. 

I think im going to be getting a network card tomorrow off a friend..

---

### Post by jvc26 on 2010-04-29
If you type ```
sudo tail -f /var/log/dmesg
``` as you plug your device in, that will let you know whether the device is recognised on plugging in. The command you asked about earlier, ```
cat /proc/usb/devices
``` is one you need to also type into terminal which can be launched from Applications->Accessories->Terminal.

J

---

### Post by jvc26 on 2010-04-29
In fact, just 

```
dmesg
```

before and after inserting the device will give you much of the information you need to see whether the device is at least recognised on plug-in.

J

---

### Post by Geoff918 on 2010-04-29
1) Alt-F2
2) Input xterm
3) cd /home/[whatever is your username]/Desktop
4) sudo lshw -html > hardware.html

On your desktop you will now have a complete rundown of the hardware in/on your computer. You can select the hardware.html document on your desktop and it will load the file in FireFox

This may help.

---

