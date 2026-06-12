---
title: "Internet connection"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by johnnie1uk on 2010-10-28
Anyone know if i should be able to get a wireless internet connection in try out mode. or do i need to install before i can check how it works.

---

### Post by migs73 on 2010-10-28
It would depend on your hardware. Some wirless cards will be supported, other require driver downloads. Best to try the LiveCD with a wired connection first, as this works 99% of the time. And you could use it to download any extra drivers you might need for your wireless.

---

### Post by KaiO on 2010-10-28
You should be able to connect to wifi also with a live cd.
You might have to provide a password - depending on your wifi setup.

---

### Post by johnnie1uk on 2010-10-28
Managed to get connected wired but not wireless.
will try loading drivers for card after i have installed
many thanks

---

### Post by amjjawad on 2010-10-28
Before you install Ubuntu, my advice to you is to find the driver first and make sure it does work before anything. At least, learn how to install it.

I usually don't install any Linux Distribution unless my Wireless Connection is supported and works perfectly. Where I keep my PC, it's not possible to connect through LAN so I must use Wireless Connection.

With the live session (LiveCD/USB), you are able to connect to the Internet by both types (Wireless and Wired).

---

### Post by johnnie1uk on 2010-11-01
Thanks, How do i check the driver works with ubuntu if ubuntu it is not installed.
wifi works fine with Windows

---

### Post by amjjawad on 2010-11-01
> **johnnie1uk said:**
> Thanks, How do i check the driver works with ubuntu if ubuntu it is not installed.
wifi works fine with Windows

1) Once you download Ubuntu from the internet, create the LiveCD or LiveUSB. Check [www.ubuntu.com](www.ubuntu.com)

2) Your 2nd step is: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3) Insert your CD or USB and reboot your machine.

4) Make sure your BIOS is set so that your machine can boot up from a CD or USB (depends on the media which you'll use - either CD or USB - your call but not that LiveUSB will be faster than LiveCD).

5) When your machine will boot form the live media (CD or USB), choose "TRY" ubuntu and do NOT install it.

6) You'll be able to test Ubuntu from the Live Media without installing it. It's not Windows, with Ubuntu and many other Linux Distributions, you can try without install.

7) If all the connections, etc will work fine, then it should work too after installing Ubuntu on your HDD.

If you need more info, please ask :)

---

### Post by migs73 on 2010-11-01
When using the liveCD and when connected to the internet (wired) goto System > Administration > Additional Drivers. This will then search for any available drivers for your system, hopefully one will be for your wireless.
If it cannot find any, or says the are installed already, post back and we'll see if we can help you along.
 If you are having problems could you open a terminal (Applications > Accessories > Terminal) and type in;

```
lspci
```

that is lower case LSPCI. This will list the cards on your PCI bus and one of those will be your wireless card. It'll let us know where to go next.
BTW terminal is not as scary as it looks, once you have your system set up you'll probably not NEED to use it again.

---

### Post by johnnie1uk on 2010-11-01
Thanks very much for the comprehensive info, i will get back if i have a problem

---

