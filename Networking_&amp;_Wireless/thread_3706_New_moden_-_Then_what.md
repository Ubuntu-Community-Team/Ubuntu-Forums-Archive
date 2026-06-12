---
title: "New moden - Then what"
date: 2004-11-08
forum: Networking &amp; Wireless
---

### Post by pref-at-laval on 2004-11-08
I just installed a modem on my Ubuntu system. IDE "Winmodem" type, is recognised as a "HSP MicroModem 56" by the Device Manager. When I go in the network setupand select the modem to connect to the internet, the check mark appears for about 1 second and then disapears. I tried changing the port to /dev/ttyS0 ... /dev/ttyS3 and it dosn't work.

Did I miss something important? Am I missing some kind of a driver?

Alain

---

### Post by az on 2004-11-09
Did I miss something?

Yes, you are not running windows.  What do you think a winmodem is?

You need drivers.

1- Check to see what chipset your modem is.  Use scanmodem:
[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

Read the output and go and get your drivers.

Conexant, Smartlink and Lucent modems have been discussed on this board earlier.  I think that a HSP Micromodem may be a pctel chipset.  If that is what scanmodem tells you is in your modem,

Go here:

[http://linmodems.technion.ac.il/pctel-linux/welcome.html](http://linmodems.technion.ac.il/pctel-linux/welcome.html)

Download this:

[http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9.tar.gz)

Install build-essential linux-headers-2.6-386 kernel-kbuild-2.6-3
These three packages are needed to build kernel modules (drivers)  If you are using a different kernel version, change the names as appropriate...

PCTEL README:
1.1 Automatic installation (for beginners)
------------------------------------------
- you must be root
- you must have installed a c compiler and development tools like
  make, perl, ...
- you must have lspci in a standard path (for automated install)
- you must have installed your kernel sources, which corresponds
  to your current running kernel


a) tar zxvf pctel-version.tar.gz

b) cd pctel/

c) ./setup

If everything was ok, you will see the message "installation done" at the
end of the output.


Now, to make sure that the modules load every time you boot: add
pctel
ptserial
to your /etc/modules file.

Good Luck!

---

### Post by pref-at-laval on 2004-11-09
I downloaded and un compressed the driver "pctel-0.9.7-9.tar.gz". Here is the error message I get:

root@ubuntu:~/pctel-0.9.7-9 # ./setup
checking for running kernel version...** error
your kernel version is: 2.6.8
this package supports only 2.4.x kernels.
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.
root@ubuntu:~/pctel-0.9.7-9 #

Any suggestions?

---

### Post by az on 2004-11-09
Ah.  


Crap.


I dont think that there is a pctel modem driver for a 2.6 kernel.


The sl-modem driver is said to work with some other chipsets.  Try that

Good luck.

Another solution would be to install a 2.4 kernel.  You could probably get one from Debian.  Like the current 2.4.27 sarge kernel.  Should play somewhat nice with Ubuntu...

---

