---
title: "Motorola SM56 PCI Modem Working"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by linitrofe on 2007-04-27
Good news!
I get my Motorola SM56 1057:3052 device working on Ubuntu Dapper Server (I guess edgy and feisty too). I left my report at:
[http://archives.linmodems.org/26589]("http://archives.linmodems.org/26589")

Tomorrow I'll write a Ubuntu Howto but all the needed info is there.

Good Luck!
Alvaro Aguirre

---

### Post by madmetal on 2007-04-27
> **linitrofe said:**
> Good news!
I get my Motorola SM56 1057:3052 device working on Ubuntu Dapper Server (I guess edgy and feisty too). I left my report is at:
[http://archives.linmodems.org/26589]("http://archives.linmodems.org/26589")

Tomorrow I'll write a Ubuntu Howto but all the needed info is there.

Good Luck!
Alvaro Aguirre

nice! got the same modem but i dont use it due to dsl line.. although it would be nice to use it for fax or backup line..

---

### Post by Mr.Ham on 2007-05-01
Congratulations, that's wonderful!  I'll be waiting for your review since I'm interested in the Motorola SM56 as well.



_________________
Tammy
[Far Circuits](http://www.who-sells-it.com/cy/far-circuits-623/far-circuits-173.html)  -  Download The Far Circuits Catalog

---

### Post by edon2007 on 2007-05-03
Hi,

I tried to patch how you described... My sm56 is 1057:3055, 
So I added some other strings... 
But it did not work. It wrote that unable to open device slamr0 and etc... 
:-(
I use notebook ASUS, HIgh Definition Audio.. 

Thanks...

---

### Post by linitrofe on 2007-05-05
Sorry for the delay but I haven't find time to write the Howto.. but
There is no big magic on setting it up. A little explanation (and I hope put a big one soon)
- Download [http://www.lino.cl/gpl/linmodems/slmodem-2.9.11-20070505.tar.gz]("http://www.lino.cl/gpl/linmodems/slmodem-2.9.11-20070505.tar.gz"), build and install
- Download [http://www.lino.cl/gpl/linmodems/ungrab-winmodem-20070505.tar.gz]("http://www.lino.cl/gpl/linmodems/ungrab-winmodem-20070505.tar.gz"), build and install
- apt-get install sl-modem-daemon
- Edit your /etc/modules and add at the tail (same order)
ungrab-winmodem
slamr
- Reboot (yeah, I know... but I try to keep it simple)

You must have now a /dev/ttySL0 device and you can use the tools you want (wvdial, ppp, minicom, etc)

---

### Post by linitrofe on 2007-05-31
I wrote the HOWTO, you can find it at [http://ubuntuforums.org/showthread.php?p=2756636]("http://ubuntuforums.org/showthread.php?p=2756636")

---

