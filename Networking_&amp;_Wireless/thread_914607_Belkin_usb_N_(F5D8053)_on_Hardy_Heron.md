---
title: "Belkin usb N (F5D8053) on Hardy Heron"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by TheProdigy2215 on 2008-09-09
Hello, I'm trying to set up a Belkin Wirless N USB device (F5D8053) on Hardy Heron.  I have tried using disgtk with rt2870 from F5D8053v1000-en.exe.  
I used wine to run the install file but it fails with a DLL error part way through.  The newer install exe fails completely but this older install file does create the Win2kXP folder containing the .inf files before failing.  I used ndisgtk to load the rt2870.inf as instructed by a forum post here but still no wireless after reboot.

Thanks in advance!

---

### Post by pytheas22 on 2008-09-09
Please do a fresh reboot, then post the output of these commands:

```
lsusb
ndiswrapper -l
uname -m
lsmod | grep ndis
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
```

That will help us figure out what's wrong.

---

### Post by TheProdigy2215 on 2008-09-11
nick@TheBeast:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 002: ID 06a3:8000 Saitek PLC 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000   
nick@TheBeast:~$ ndiswrapper -l
rt2870 : driver installed
nick@TheBeast:~$ uname -m
i686
nick@TheBeast:~$ lsmod | grep ndis
nick@TheBeast:~$ 
nick@TheBeast:~$ lsmod | grep ndis
nick@TheBeast:~$ sudo modprobe ndiswrapper
[sudo] password for nick: 
nick@TheBeast:~$ dmesg | grep -e ndis -e wlan
[27429.092841] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[27429.129290] usbcore: registered new interface driver ndiswrapper
nick@TheBeast:~$

---

### Post by Crafty Kisses on 2008-09-11
First off, try using an earlier driver for this card, you can get it right [**here**]("http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz"). After you have installed the drivers, you might want to look for the .inf file, you said you already used **"ndisgtk" ** and it didn't work, so what I want you to do is remove ndisgtk by doing the following:
```
sudo apt-get remove ndisgtk
```
Then reinstall it by doing: ```
sudo apt-get install ndisgtk
```
After that has been done, make sure you have this package installed:
```
sudo apt-get install linux-headers
```
After you have done all that, open up **ndisgtk** and try reinstalling the .inf file through there, and see if that does it for you. Remember the driver provided is a little older, so try it.

---

### Post by pytheas22 on 2008-09-11
What the poster above says is true.  ndiswrapper doesn't think that the Windows driver that you installed is the right one, so you'll need to get the right one.  A second problem is that ndiswrapper doesn't appear to be loading automatically at boot.  You can rectify that by running:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

If after installing the new driver things don't work, please post:
```

lspci -nn
lshw -C Network
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

> After that has been done, make sure you have this package installed:
Code:

sudo apt-get install linux-headers


@Codename:

Just out of curiosity (because I've never heard this before), why do you need the kernel headers installed to run ndiswrapper (unless you were compiling it, but no one is here)?

---

