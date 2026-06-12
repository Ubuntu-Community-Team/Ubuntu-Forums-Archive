---
title: "Compag HP nx7400 - BCM4311 WIFI is very slow! ubuntu 12.04."
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by mafeuser on 2014-10-06
Hello people!
 my case is very simillar to the one closed:
[http://ubuntuforums.org/showthread.php?t=2126876](http://ubuntuforums.org/showthread.php?t=2126876) 

in short:
I'm running ubuntu 12.04. My WIFI card is:
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

way 1:
sudo apt-get --reinstall install bcmwl-kernel-source
gives kernel panic:
kernel BUG at "include/net/cfg80211.h:2209!"

way 2:
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer

makes WIFI connection succeed, but internet on that is very, very slow. It is unusable. I checked it on number of WIFI routers which I'm sure work ok. It is NOT the problem of poor signal. This is not the problem of WIFI card device in my HP (see below). The problem seem to be exacly the same as in thread `2126876' mentioned at the beginning of my post.

way 3:
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install linux-firmware-nonfree

this way was working correct for more than a year until last update.
Why did it stop working?
because b43 driver seem to be removed from linux-firmware-nonfree package.

I'm stuck with this problem.

I need Your help please.

regards,
Maf

---

### Post by mafeuser on 2014-10-11
in the meantime I tried to compile newest STA driver.
Unfortunatelly no luck. I got kernel panic: [https://www.mediafire.com/?0l5924b5373zamv](https://www.mediafire.com/?0l5924b5373zamv)

I did theses steps:
download newest driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), unpack it and cd..
ubuntu.12.04$ make
ubuntu.12.04$ sudo make install
ubuntu.12.04$ sudo depmod -a
ubuntu.12.04$ sudo rmmod b43 b44 ssb #. I should also remove: wl, bcma, brcmsmac, but they were not loaded in my system, so no need to do this
ubuntu.12.04$ modprobe wl #. produces kernel panic mentioned above.

---

### Post by Hadaka on 2014-10-11
Hi, here is a guide for future use for you ..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

open a terminal...ctrl/alt/t...and connect to the internet via
your wired connection,,,then enter these commands,,,one at a time
even if you get a fail, or error enter it anyway..one line at a time.
Please COPY and paste..one line at a time,

```
sudo apt-get update
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer 
```
then do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```



@Jermy31-thanks for the catch on the typo
sometimes that file is not deleted-and i have no idea how many different
drivers were attempted,so i tossed it in for good measure.

---

### Post by jeremy31 on 2014-10-11
> **Hadaka said:**
> Hi, here is a guide for future use for you ..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

open a terminal...ctrl/alt/t...and connect to the internet via
your wired connection,,,then enter these commands,,,one at a time
even if you get a fail, or error enter it anyway..one line at a time.
Please COPY and paste..one line at a time,

```
sudo apt-get update
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge linux-frmware-nonfree
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer 
```
then do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```

We have a typo instead of ```
sudo apt-get remove --purge linux-frmware-nonfree
``` it should be ```
sudo apt-get remove --purge linux-firmware-nonfree
```

And why doesn't ```
sudo apt-get purge bcmwl-kernel-source
``` delete the /etc/modprobe.d/ file it created.  I think the latest is /etc/modprobe.d/[COLOR=#2E8B57][FONT=Monaco]broadcom-sta-common.conf[/FONT][/COLOR]

---

### Post by chili555 on 2014-10-11
> And why doesn't
Code:
sudo apt-get purge bcmwl-kernel-source
delete the /etc/modprobe.d/ file it created. I think the latest is /etc/modprobe.d/broadcom-sta-common.conf'purge' removes the file it created on installation; /etc/modprobe.d/blacklist-bcm43.conf .

---

### Post by Otto-C on 2014-10-13
Open terminal and do:
$ lspci -vvnn | grep 14e4
Will show card model and network controller info.
$ dmesg
Look for b43 error well down the page.
Will have you goto a page with instructions to follow
for Ubuntu/Debian. Copy and paste command in
terminal. After install reboot. Create wireless network
if needed.

Keep us posted.
hth
otto-c

---

### Post by mafeuser on 2014-10-18
Hadaka,
I just issued all the commands You mentioned, with -firmware- typo fixed of course.

I think I understand the difference. This time new driver has been downloaded:
[http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)

Now it's the time for testing. I'll let You know about the results.

Thank You so far for good direction.

Regards,
Mafeos

---

