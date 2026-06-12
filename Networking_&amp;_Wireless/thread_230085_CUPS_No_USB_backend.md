---
title: "CUPS: No USB backend"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by fene on 2006-08-05
Hi. I'm using an old notebook (Compaq Armada 1592DT) as server. There's a Dapper Ubuntu installed. I'm just using the server for Samba and Cups. A few days ago I bought a Brother HL-2030 monochrome laser printer that I wish to connect to the local USB port of the server. Later I'd like to share it among all the network users. Now let's talk about the problem:

Cups doesn't use the USB backend and I have no clue why. That's why I'm not able to configure the printer in the Cups Web Interface. I've a valid PPD file that works fine on other computers.

lpinfo -v just shows the following lines (usb is missing):
```
network socket
network http
network ipp
network lpd
direct parallel:/dev/lp0
network smb

```

the kernel modules **usblp** and **usbcore** are loaded.
lsusb shows that the printer is plugged to computer:
```
Bus 001 Device 004: ID 04f9:0027 Brother Industries, Ltd
Bus 001 Device 001: ID 0000:0000

```

And dmesg shows as well that a usb device is connected:
```
Aug  5 15:55:16 srvlochm kernel: [181422.874966] usb 1-1: new full speed USB device using ohci_hcd and address 4
```

As mentioned I've no clue why this problem occures and I'd really appreciate every hint that could solve this problem in order to make Cups seeing the USB backend. Thanks loads in advance.

---

### Post by sitedesign on 2006-08-05
I am using CUPS with 2 USB printers at work. It is sharing the USB printers with Windows PC's, MAC's and Linux work stations. So CUPS does support USB.

The server at work is running Debian 3.1 so should be similar.

I have just tried plugging a USB printer into my Laptop running Dapper and it sees the printer no problem.

lpinfo -v

network socket
network beh
network bluetooth
direct usb://Dell%20/Photo%20AIO%20922
network http
network ipp
network lpd
network smb

I know the Del 922 will never work under Linux though. Gave up on that months ago.

---

### Post by fene on 2006-08-06
Thank you for your reply. Yes, i know, this is the way it should work (and of course in most cases it does work). But my problem is that the cups deamon doesn't want to use the usb backend respectively doesn't recognize the printer on the usb port.

Does anybody has hints or ideas how to fix this problem? I'm not too experienced in hacking cups or troubleshooting hardware issues in linux.

---

### Post by sitedesign on 2006-08-07
O you mention that the laptop is a server. Is it running the desktop edition of Dapper or the server edition?

My previous reply was from my laptop running Dapper desktop. I also have Dapper server on a machine at work which I can test pluggin a USB printer into to check the USB in CUPS on the server edition works.

Also just in case of version differences, post back the response from uname -a (gives the kernel details), and the response to dpkg-query -p cupsys
 (version of cups installed).

---

### Post by craiger316 on 2006-08-17
I am having a similar problem as well.  USB does not show up as a valid port when I try to add a new printer via the cups config application.  Yet, I do have USB (the mouse is running off usb), but cups doesn't know about it.

The only thing I can think of is when I installed ubuntu the printer wasn't plugged in, but that doesn't make sense, you would think cups would just go "oh usb port, at some point a printer might live there"

Any idea how to resolve this?

Thanks,

Craig.

---

### Post by bajun on 2007-12-29
By trying to connect Epson Stylus Color 300 with my laptop i have the same problem. Any ideas?

---

### Post by tturrisi on 2007-12-29
open a term and
/etc/init.d/cupsys start
open a browser and go to
[http://localhost:631](http://localhost:631)
& setup your priners

---

### Post by bajun on 2008-01-03
Nothing has changed after restart CUPS. No USB in CUPS. Problem details: [http://ubuntuforums.org/showthread.php?t=656394]("http://ubuntuforums.org/showthread.php?t=656394")

---

### Post by bajun on 2008-01-09
After reinstall of ubuntu on clear installation all works fine. My printer was detected and work completly with CUPS. I can setup USB printer. Something was broken?

---

