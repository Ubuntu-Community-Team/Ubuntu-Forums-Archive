---
title: "[SOLVED] Ubuntu 8.10 to 8.04 switch"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by AkiraBergman on 2008-12-18
I bought a Logitech Pro 9000 webcam without checking it's support on 8.10 unfortunately. I tried few things but I got nowhere. Apparently it works out of the box on 8.04.

What is the easiest way to switch back to 8.04? I got the 8.04 CD and I have a spare hard disk.

---

### Post by phantomjoker on 2008-12-18
personally, because i have had experiance with peripherals which say they work with linux, but dont - i would try the 8.04 live disk and see if it works, if it does THEN go through the installation. But if you just want to get on with it, then just install it on the blank HDD.

Why are you switching back for a webcam - can't you just take it back and get a new one?

---

### Post by prshah on 2008-12-18
> **AkiraBergman said:**
> I bought a Logitech Pro 9000 webcam
unfortunately. I tried few things but I got nowhere

Before that, try this;

plug in the webcam, then open a terminal (Applications-Accessories-Terminal) and give the command ```
lsusb
dmesg | tail
```

Some people have found that USB devices are detected only after a "lsusb" command, for some peripherals. 

Also post back the results of the above two commands.

---

### Post by AkiraBergman on 2008-12-18
> **prshah said:**
> Before that, try this;

plug in the webcam, then open a terminal (Applications-Accessories-Terminal) and give the command ```
lsusb
dmesg | tail
```

Some people have found that USB devices are detected only after a "lsusb" command, for some peripherals. 

Also post back the results of the above two commands.

Yes it worked a bit with Cheese. It brings up the video, takes snapshots, but does not record video. When you hit 'start recording' the Cheese screen goes black. After 'stop recording' it creates an empty file.

Cameroma does not work.

Here is the terminal response to the commands;

nuri@yilmaz:~$ lsusb
Bus 005 Device 004: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nuri@yilmaz:~$ dmesg | tail
[ 2181.172102] uvcvideo 5-2:1.1: resume error -5
[ 2181.172867] PM: Image restored successfully.
[ 2181.237071] Restarting tasks ... done.
[ 2181.241176] PM: Basic memory bitmaps freed
[ 2182.594746] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2182.596422] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[ 2182.596830] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2183.241896] 4:3:1: usb_set_interface failed
[ 2183.620831] [fglrx] It's not necessary to adjust system aperture on this ASIC 
[ 2192.772008] eth0: no IPv6 routers present
nuri@yilmaz:~$

---

### Post by AkiraBergman on 2008-12-18
> **phantomjoker said:**
> personally, because i have had experiance with peripherals which say they work with linux, but dont - i would try the 8.04 live disk and see if it works, if it does THEN go through the installation. But if you just want to get on with it, then just install it on the blank HDD.

Why are you switching back for a webcam - can't you just take it back and get a new one?

Live disk did not work. I installed 8.04 on the spare disk. Cheese works!!!! The sound is a bit too low but it is there. Thanks.

---

