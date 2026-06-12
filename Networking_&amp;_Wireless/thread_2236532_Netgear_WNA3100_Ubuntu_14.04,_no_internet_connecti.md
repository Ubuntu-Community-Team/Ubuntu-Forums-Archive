---
title: "Netgear WNA3100 Ubuntu 14.04, no internet connection"
date: 2014-07-27
forum: Networking &amp; Wireless
---

### Post by willn2010 on 2014-07-27
Hello, Ubuntu users. This is my first forum post. I have not used Ubuntu in many years, and recently decided to go back to it. However I cannot get my WiFi drivers to work. I have no way to access the internet on my Ubuntu installation, so I need to download files and such in windows and save them to a flash drive.

What I was able to find out is that it is a Broadcom USB adapter, so I know I will have to use NDISWRAPPER.

What I am basically asking for is if someone could send me links to direct downloads for all of the files that I need, and terminal commands to get it working.

Any help will be greatly appreciated. I have searched Google for literally days, and I have not found anything.

Thanks
-Will

---

### Post by Vladlenin5000 on 2014-07-27
Hi, welcome.

You can start by browsing this thread, it lists what is needed: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)
If you have an Ethernet connection the best you can do is use it for installing what's needed. Better yet is to ditch that old hardware. You can get a fully supported OOTB USB dongle for US$10 or less.

---

### Post by Rob Sayer on 2014-07-28
> **willn2010 said:**
> ... What I was able to find out is that it is a Broadcom USB adapter, so I know I will have to use NDISWRAPPER...

I don't know where you read this but you need to start finding better sources, which I know is hard for newbies.  I have a laptop and a netbook with 2 different Broadcom wireless cards.  One has had a lot of hardware support issues in the past.  The other has never, ever had any trouble whatsoever.

The problem with the above link on your netgear adapter is that those guys have a bad habit of changing the actual adapter in their device with no warning.

So before proceeding with that link open a terminal and paste this into it:

```
sudo lshw -C network
```

and enter your password.  It'll take a second but it'll tell you what device it is (wlan0).

---

### Post by ekmorton1947 on 2014-08-10
I have worked on this for several days, I was about to take my usb back!  my driver was changed to Broadcom Bcmn43xx32.inf and I ran ndiswrapper to install file. The last thing I did was to OPEN my Netgear Router and change my setting from WPA2 AES to WPA2(TKIP), applied it, and it started to initiate my USB. Try this and see if it works.

---

