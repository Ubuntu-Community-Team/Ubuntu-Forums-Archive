---
title: "Unable to configure Tata photon (usb Mobile wireless)connection in ubuntu10.04"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by vaibhavrohal on 2010-10-09
Hi,

I am new to linex. i Have installed the Ubuntu 10.04.1 LTS
Codename:  lucid

I installed with usb drive.

After running the command sudo apt-get install wvdial

i gets the message wvdial package not available.

On Installating the wvdial-1.60.3-i386.deb
error message is: Dependency is not satisfiable.:libuniconf4.6

My system as well has the working windows xp . processor is intel with 1 gb ram.


with these i have even installed the 2 packages of usb-mdeswitch-data but my device is not being detected by the network manager.

Require help to setup the usb mobile broadband connection.

---

### Post by Hippytaff on 2010-10-09
> 
Dependency is not satisfiable.:libuniconf4.


try doing

```

sudo apt-get install libuniconf4

```

might also be worth doing a
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by vaibhavrohal on 2010-10-09
On running all these commands following two error message are coming.

:could not get lock/var/lib/dpkg/lock - open (11: Resource temporarily unavailable)

:Unable to lock the administration directory (/var/lib//dpkg/), is another process using it?

---

### Post by Hippytaff on 2010-10-09
Thats beyond my knowledge...may be worth just upgrading to 10.10....out in about 10 minutes :-)

---

### Post by Hippytaff on 2010-10-09
though some other people here have a far advanced knowledge of this than me....so keep posting

---

### Post by vaibhavrohal on 2010-10-10
Reinstalled the ubuntu 10.04.  Now Tata photon (usb internet drive)
is detected & shown in the network manager. But on pressing the connect in NM. it tries to connect but not able to establish the connection.
Please suggest the remial measures.

---

### Post by Hippytaff on 2010-10-11
What is the output of the following - 
 
```

lsusb

```
 
```

lshw -c Newtork

```
 
```

iwconfig

```

---

### Post by vaibhavrohal on 2010-10-12
Thanks for all the valuable suggestions. My problem is sorted out.

---

### Post by Hippytaff on 2010-10-12
> **vaibhavrohal said:**
> Thanks for all the valuable suggestions. My problem is sorted out.
 
Excellent - remember to mark your thread as solved in the thread tools at the top of the page

---

### Post by harishsudharsan on 2011-07-14
Guys. Its not a big deal at all. Finally I got it to work easily on Ubuntu 10.04

1. Download the usb-modeswitch-1.1.8.tar.bz2 and usb-modeswitch-data from [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) and follow the installation instruction on the website. (sudo make install stuff)

2.Restart your computer and thats all.

3.Every time you disconnect you don't have to restart your computer. Just unplug and replug your photon!

---

