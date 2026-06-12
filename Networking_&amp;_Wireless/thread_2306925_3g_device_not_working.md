---
title: "3g device not working"
date: 2015-12-20
forum: Networking &amp; Wireless
---

### Post by marouane87 on 2015-12-20
Hello :)

I have just made a fresh installation of Ubuntu Gnome 15.10. Everything is fine except for my 3g device that I couldn't use to connect. It's a Huawei E1752.
I made the steps of adding a new Broadband mobile device and added the service provider etc... But Broadband connection is always "unavailable" on the top right.
In addition, when I go to network manager and click on "edit" for the new added Broadband connection, I have the following error message:
> Error initializing editor
settings/nm-settings-connection.c.955 - Connection didn't have requested setting 'ppp'.


The device seems to recognised by Ubuntu since lsusb returns:
> marouane@marouane-X555LAB:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 13d3:3423 IMC Networks 
Bus 001 Device 003: ID 04f2:b483 Chicony Electronics Co., Ltd 
_Bus 001 Device 013: ID 12d1:141b Huawei Technologies Co., Ltd. _
Bus 001 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Any help would be appreciated :)

Note: This same device gets recognised and worked fine in Linux Mint (16/17/17.1/17.2 and 17.3)

Thank you!

**_EDIT : Solution:_** I tried to disable the PIN authentication (I used Windows to do so, since the device has its own application on it), and it worked when I got back to Ubuntu :) (Another workaround, it seems that KDE supports PIN authentication, so using KDE may also works)

---

### Post by praseodym on 2015-12-21
Please check:
```

usb-devices
lsmod
ifconfig -a
```
Did you install usb-modeswitch? Is it shown under "cable connection"? Can you enter a web interface to configure?

---

### Post by marouane87 on 2015-12-21
Thank you, but I'm sorry I had to find a solution and got back to Mint 17.2 to get a connection... I wouldn't be able to answer for the commands For the second part, usb_modeswitch was installed along with modem manager. 
It was shown under "Broadband connection" and marked just next to it "unavailable". And no, I can't open a web interface to configure it. 
Normally in mint, as soon as I plug it, a windows pops up asking for PIN code, that doesn't even happen in Ubuntu gnome.
The pin window:
[img]http://s10.postimg.org/sih8t3f61/pin.jpg[/img]

---

### Post by praseodym on 2015-12-21
You can temporarily enter the PIN once via terminal

```
mmcli -i 0 --pin=xxxx
```
Change xxxx with your PIN. Disable it permanently via

```
mmcli -i 0 --disable-pin --pin=xxxx
```
if applicable.

---

### Post by marouane87 on 2015-12-25
Thank you, as I said, I installed back Mint 17.2 (which is based on Ubuntu LTS 14.04.1).

Meanwhile, I tried Arch on a Virtual Box, and it also doesn't detect the device (using lts kernel 4.1 or 4.2, I'm not sure). But using sakis3g it worked on both Arch and Ubuntu 15.10. (This might help other people if they can't find a solution and want to use this latter).

Just out of curiosity if anyone can answer, what does sakis3g do and not usb-modeswitch and modem manager for 3g connection success :) ?

---

### Post by praseodym on 2015-12-25
sakis3g works with usb-modeswitch and a dial-in script, but I don't know how it exactly works. You may google for it?!

Happy holidays!

---

### Post by marouane87 on 2015-12-25
Thank you very much.
I had some free time, so I wanted to test this problem on OpenSuse 42.1. And I had the same issue (except that the Broadband kept "Off" instead of "Unavailable"). On the other hand, on KDE, it worked (kind of... KDE kept asking for PIN, and gnome never asked for it)...
At this point, I'm starting to think about a problem in Gnome Network Manager (if it is not the same used on 14.04 and 15.10). Is there anyway to be sure please?

Thanks!

Edit: I tested Also on Kubuntu 15.10 and it worked. So, I opened a ticket to network manager team for further investigation.

---

