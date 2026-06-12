---
title: "Dell wireless 1395 Vostro 1500"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Phoenix8907 on 2008-07-07
First off all, I'm a noob. So go easy please.

I have a Dell Vostro 1500 with a 1395 dell wireless minicard for my wifi. I have gotten it to respond and work correctly once before, but I had to nuke my laptop and I can't seem to figure out how I did it last time. Any assistance would be helpful. I can give you more specific information about the system if you are willing to help.

Thanks.

---

### Post by stats on 2008-07-07
I have the same card.
do this
```
sudo apt-get install ndisgtk
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

since you know you have the 1395, goto the dell site and download the windows XP (NOT vista) drivers for the 1395 card

now goto the directory where u downloaded it and unzip <name of the file>

now in the top menu
System | Administration | Windows wireless drivers
choose the bcmwl5.inf file(it will be in one of the folders of the unzipped file)
close the dialog, open a terminal and type  
  ndiswrapper -l
you should see
  Installed ndis drivers:
  {name of driver} driver present, hardware present

or

  {name of driver} : driver installed
       device ({Chipset ID}) present

now follow instructions from section 3.5 of
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Phoenix8907 on 2008-07-07
I downloaded the driver, located the bcmwl5.inf file, and it told me it was an "invalid driver." Any advice?

---

### Post by fmlouge on 2008-07-08
I had the same problem, but I was able to solve it using the driver for a 1390 card. Here's the link: [ftp://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe]("ftp://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe")

---

### Post by Phoenix8907 on 2008-07-13
Here is exactly what I'm doing.

Download the A17 R174291 Driver to my desktop.

Using wine, I extract the files to my C Drive.

Accessing my C drive, I copy the bcmwl5.inf to my desktop.

Using the wireless network drivers, I install bcmwl5.inf.

Result: Invalid Driver.


It still is not working.

---

### Post by Phoenix8907 on 2008-07-13
The dell driver for the 1390 and the 1395 is the same driver by the way.

Dell Wireless 1395 WLAN MiniCard
Driver
Release Title:	Network: Dell Wireless 1370 WLAN MiniPCI Card, Wireless 1390 WLAN MiniCard, Wireless 1395 WLAN MiniCard, Wireless 1470 Dual-Band WLAN miniPCI Card, Wireless 1490 Dual-Band WLAN MiniCard, Wireless 1505 Draft 802.11n WLAN Mini-Card, Wireless 1505 Draft 802.11n WLAN Mini-Card Desktops, Driver, Windows XP, Windows XP x64, Multi Language, Multi System, v.4.170.25.12, A17
Release Date:	12/18/2007
Criticality:	Recommended
Description:	This release supports the Dell Wireless 1350, 1370, 1390, 1395, 1450, 1470, 1490, 1500, 1505 series Mini Card, MiniPCI and PC Card devices (not USB).

By downloading, you accept the terms of the Dell Software License Agreement.

File Name	File Size	Download Time (56K)	File Format
Dell_multi-device_A17_R174291.exe	89 MB	3.7 hr	Hard-Drive

---

### Post by Phoenix8907 on 2008-07-15
*bump*

---

### Post by Phoenix8907 on 2008-07-15
Does anybody know what I can do?

---

### Post by alien0101 on 2008-07-16
Hi Pheonix,

Are you able to solve the problem?
I am having same configuration notebook.
I am able to see wireless networks but cannot connect to WPA network..

---

### Post by alien0101 on 2008-07-16
You can try to upgrade pacakges and then use restricted wireless driver.

If you able to connect to WPA network , let me know.

---

### Post by Phoenix8907 on 2008-07-16
So far nothing I have tried has worked. I did a little reasurch, and come to find out, I think there is an update conflict with this driver. I'm not sure if it is Dell or Ubuntu's fault.

---

### Post by Phoenix8907 on 2008-07-16
I don't know what I did, but it worked! If you need some help, use the advice from other in this thread, and there are a few more references that I can give you if you want/need them.

---

### Post by alien0101 on 2008-07-17
Yeah sure please send me the links of other thread from where u took references.

CAn you tell me which driver u using. Currently I am using wl restricted driver.
I am able to connect to unsecured wireless but not WPA network.

Have you tried some other linux disto? Any experiences with them?

Please let me know any steps if u can recall..

---

### Post by gausjord on 2008-08-01
Bump...

I'm interested to see what Phoenix has done to this to work...details!

I'm running a Dell D400 with the wireless 1450 miniPC.  I've tried the b43-fwcutter technique to no avail, but I guess I'll go back to the first page of this thread and try the Ndisgtk (ndiswrapper) option.  I've downloaded the R1407045.exe from dell.com, and will attempt to use the inf and sys files from that.

Be back in a few...

---

### Post by armine on 2008-09-20
> **Phoenix8907 said:**
> I don't know what I did, but it worked! If you need some help, use the advice from other in this thread, and there are a few more references that I can give you if you want/need them.



Hi Phoenix8907

I have the same PC and the same wireless mini card and the same problem you had - no wireless on Ubuntu. Please, please, help me .... how you did it? 

Thanks a lot

---

