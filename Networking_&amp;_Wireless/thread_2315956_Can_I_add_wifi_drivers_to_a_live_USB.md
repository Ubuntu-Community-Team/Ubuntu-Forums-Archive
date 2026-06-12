---
title: "Can I add wifi drivers to a live USB?"
date: 2016-03-04
forum: Networking &amp; Wireless
---

### Post by vasa1 on 2016-03-04
My situation is this. I have an oldish Dell Inspiron 1545 laptop (from ~2009). In order to get wifi to work, I had to install b43-fwcutter and firmware-b43-installer while connected to the internet via cable. Then, IIRC, a lot of files were installed and I could switch to wifi for connectivity.

Because of security measures enforced by my ISP, I can no longer switch from wifi to cable or vice versa easily from home. To do so, I have to visit my ISP's office each time.

My question is this: can I just copy over relevant driver files/folders from my existing 14.04 installation to the corresponding location on a live USB of _16.04_ to make this live USB access the internet via wifi when I boot via the live USB? 

A [post by carl4926]("http://ubuntuforums.org/showthread.php?t=2216631&p=12985955#post12985955") suggests that something like that is possible.

I didn't try it at the time. I chickened out and visited my ISP to get wifi going after I installed Ubuntu 14.04 using cable. My laptop will be next to my router and so I don't anticipate any poorer connectivity using wifi rather than cable.

Now, I can run
```
cd /lib/firmware && ls -l
```but I can't change directory to b43 and I can't copy the b43 folder to my home.

```
10:37 AM /lib/firmware $ cd b43
bash: cd: b43: Permission denied
10:39 AM /lib/firmware $ cp b43 ~/Desktop
cp: omitting directory ‘b43’
10:39 AM /lib/firmware $ sudo cd b43
[sudo] password for vasa1: 
sudo: cd: command not found
10:39 AM /lib/firmware $ sudo cp b43 ~/Desktop
cp: omitting directory ‘b43’
10:40 AM /lib/firmware $ sudo cp b43 ~/Desktop/
cp: omitting directory ‘b43’
10:40 AM /lib/firmware $ 

```
Details of the b43 folder are this:```
10:33 AM /lib/firmware $ cd /lib/firmware/ && ls -l
total 42740
drwxr-xr-x 11 root root    4096 Nov 14  2014 3.13.0-39-generic
drwxr-xr-x 11 root root    4096 Feb  2 07:00 3.13.0-77-generic
drwxr-xr-x 11 root root    4096 Feb 23 06:25 3.13.0-79-generic
drwxr-xr-x  2 root root    4096 Jan 21 06:56 3com
drwxr-xr-x  2 root root    4096 Jan 21 06:56 acenic
drwxr-xr-x  2 root root    4096 Jan 21 06:56 adaptec
drwxr-xr-x  2 root root    4096 Jan 21 06:56 advansys
-rw-r--r--  1 root root   50698 Nov 24  2014 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 Nov 24  2014 agere_sta_fw.bin
drwxr-xr-x  2 root root    4096 Jan 21 06:56 ar3k
-rw-r--r--  1 root root  153416 Dec  1  2014 ar5523.bin
drwxr-xr-x  2 root root    4096 Jan 21 06:56 asihpi
drwxr-xr-x  3 root root    4096 Jul 23  2014 ath10k
-rw-r--r--  1 root root  246804 Jan  6 21:10 ath3k-1.fw
drwxr-xr-x  4 root root    4096 Jul 23  2014 ath6k
-rw-r--r--  1 root root   35180 Jan  6 21:10 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 Jan  6 21:10 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root    9726 Nov 24  2014 atmsar11.fw
drwxr-xr-x  2 root root    4096 Jan 21 06:56 av7110
**drwxr-x---  2 root root    4096 Nov 14  2014 b43**
drwxr-xr-x  2 root root    4096 Jan 21 06:56 bnx2x
drwxr-xr-x  2 root root    4096 Jan 21 06:56 brcm
-rw-r--r--  1 root root   13388 Dec  1  2014 carl9170-1.fw
drwxr-xr-x  9 root root    4096 Jan 21 06:56 carl9170fw
-rw-r--r--  1 root root  412528 Nov 24  2014 cbfw-3.2.1.1.bin
-rw-r--r--  1 root root  414016 Nov 24  2014 cbfw-3.2.3.0.bin
drwxr-xr-x  3 root root    4096 Jan 21 06:56 cis
-rw-r--r--  1 root root     107 Dec  1  2014 configure
drwxr-xr-x  2 root root    4096 Jan 21 06:56 cpia2
... more files and folders omitted 
```

Edit: I don't think the b43 folder is somehow locked because I'm using wifi. In the thread I linked to earlier, I couldn't access the b43 folder even when I wasn't using wifi.

---

### Post by Bucky Ball on 2016-03-04
*Thread moved to **Networking & Wireless**.*

If your computer is going to be right next to the router I'm wondering about your reasons for preferring wifi. A cable is more reliable and faster (I wouldn't be doing a release upgrade via wireless, for instance, and it is certainly not advised). :-k

---

### Post by sudodus on 2016-03-04
The new Ubuntu family iso files contain several drivers, that are not ported automatically to an installed system. Try Xenial Xerus live - it might work out of the box with your wifi chip :-)

---

### Post by vasa1 on 2016-03-04
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless**.*

If your computer is going to be right next to the router I'm wondering about your reasons for preferring wifi. A cable is more reliable and faster (I wouldn't be doing a release upgrade via wireless, for instance, and it is certainly not advised). :-k

I have a smartphone as well and use wifi on that. Because I can't have both wifi and cable at the same time I opted for wifi. Though for the upgrade or new installation I may just have to visit the ISP.

> **sudodus said:**
> The new Ubuntu family iso files contain several drivers, that are not ported automatically to an installed system. Try Xenial Xerus live - it might work out of the box with your wifi chip :-)

Thanks for that, if they've provided my particular driver that would be neat!

---

### Post by Hadaka on 2016-03-04
Hi, I just did this a few days ago with the b43 driver so hopefully 
we can get you going. First i need some info, and it is important that
you follow direction exactly.remove the live usb from your computer and then
boot to normal accesss to the net like you do daily. once you are up and online
then and only then, insert the the usb stick and enter this command...
```
df -h
``` this shows both your internal hard drive and the usb info.
copy and paste the output and we will go from there. This is really simple once
we have the correct information.
thanks.

---

### Post by vasa1 on 2016-03-04
@Hadaka, thank you for offering to help but I'm not ready now. I posted my query just to find out things in advance. If you don't mind, I'll PM you after 16.04 is released and if you're free then your help will be most welcome!

---

### Post by Hadaka on 2016-03-04
OK, no problem, be glad to help. By the way, looking at the commands you have
posted I can tell what you are trying to do, but that is not the correct way, there
is no need to copy to the Desktop. The directory /lib/firmware/b43 is a root directory,
messing around in there you run the risk of corrupting your only working b43 file. Let
us know when you are ready.

---

### Post by vasa1 on 2016-03-04
> **Hadaka said:**
> OK, no problem, be glad to help. By the way, looking at the commands you have
posted I can tell what you are trying to do, but that is not the correct way, there
is no need to copy to the Desktop. The directory /lib/firmware/b43 is a root directory,
messing around in there you run the risk of corrupting your only working b43 file. Let
us know when you are ready.Thank you, will do :)

---

