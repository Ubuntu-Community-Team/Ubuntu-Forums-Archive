---
title: "can't install netgear"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by altvic on 2009-01-02
attempted to install a wireless driver for netgear wpn111 but got yhe following:

altvic@altvic-desktop:~$ tar xvvf wpn111_1_1.exe
tar: wpn111_1_1.exe: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
altvic@altvic-desktop:~$

---

### Post by handydan918 on 2009-01-02
> **altvic said:**
> attempted to install a wireless driver for netgear wpn111 but got yhe following:

altvic@altvic-desktop:~$ tar xvvf wpn111_1_1.exe
tar: wpn111_1_1.exe: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
altvic@altvic-desktop:~$
You are not going to succeed in trying to run a windows executable under linux to install a driver. 
Have you tried just using the device? If Ubuntu recognizes it, it may just work. 
If it doesn't work, plug it in, and give us the output of ```
lspci
```

---

### Post by ibutho on 2009-01-02
Native Linux drivers are probably better IMHO. What is the ouput of running
```
sudo lspci | grep -i net
```
and
```
sudo lshw -C network
```

---

### Post by altvic on 2009-01-02
altvic@altvic-desktop:~$ sudo lspci | grep -i net
[sudo] password for altvic: 
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
altvic@altvic-desktop:~$


altvic@altvic-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       logical name: eth0
       version: 82
       serial: 00:07:95:5b:7b:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.4 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
altvic@altvic-desktop:~$

---

### Post by LowSky on 2009-01-02
if it usb then we need the output of
```
lsusb
```

lspci will only sohw internal wireless

---

### Post by altvic on 2009-01-02
altvic@altvic-desktop:~$ lsusb
Bus 002 Device 003: ID 1385:5f01 Netgear, Inc 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
altvic@altvic-desktop:~$

---

### Post by LowSky on 2009-01-02
i just check around the net. it seems that a program called madwifi should be able to get your wireless working. Its availible in the ubuntu repos... good luck

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

---

### Post by jerome1232 on 2009-01-02
> **altvic said:**
> attempted to install a wireless driver for netgear wpn111 but got yhe following:

altvic@altvic-desktop:~$ tar xvvf wpn111_1_1.exe
tar: wpn111_1_1.exe: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
altvic@altvic-desktop:~$

If that .exe happens to be a self-packaging archive and you were trying to extract the .inf file to work with ndiswrapper then there's a few ways to get the .inf file out.

Run the .exe with wine, the .inf should get extracted to a tmp directory.

I've heard unzip can extract file's from .exe's as well (if it's that type of .exe)

```
unzip */path/to/the.exe/file*
```

---

### Post by altvic on 2009-01-02
sorry but this is where I struggle.  Page is just gobbledegoop to me.  Anyway, any help to give me hand holding help will be appreciated.
Thanks

---

### Post by altvic on 2009-01-02
the file I want is on the desktop but I do not understand how to fill in the instructions you give.

unzip /path/to/the.exe/file

---

### Post by jerome1232 on 2009-01-02
then it would be
```
unzip ~/Desktop/*nameoffilehere*
```

change nameoffilehere to the actual name of the file of course. I can't guarantee that will get the .inf file out. Only works on certain types of Windows Executables. Won't hurt anything to try though :)

---

### Post by altvic on 2009-01-03
Didn't work - any other ideas to get netgear working?

altvic@altvic-desktop:~$ unzip ~/Desktop/wpn111_i_1.exe
unzip:  cannot find or open /home/altvic/Desktop/wpn111_i_1.exe, /home/altvic/Desktop/wpn111_i_1.exe.zip or /home/altvic/Desktop/wpn111_i_1.exe.ZIP.

---

### Post by altvic on 2009-01-04
can someone please help get me online? via netgear EPN111 v1.1
Many thanks

---

