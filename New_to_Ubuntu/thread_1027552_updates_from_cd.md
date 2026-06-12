---
title: "updates from cd"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by klein de usa on 2009-01-01
hi 
i'm wondering if there is a way of downloading all the updates from the internet for ubuntu 8.10 i386 till now, and put them on a cd, so everytime i install ubuntu 8.10 i don't have to download the 230mb each time?

---

### Post by jpkotta on 2009-01-01
Most updates are cached in /var/cache/apt/.

---

### Post by oilchangeguy on 2009-01-01
> **klein de usa said:**
> hi 
i'm wondering if there is a way of downloading all the updates from the internet for ubuntu 8.10 i386 till now, and put them on a cd, so everytime i install ubuntu 8.10 i don't have to download the 230mb each time?

even if you could, why? because new updates are added all of the time. so you'll still at some point be prompted to install updates. and with a highspeed connection it does not take long.

---

### Post by presence1960 on 2009-01-01
go to add/remove and install apton cd. But this will only put on cd the packages currently installed on your machine.

---

### Post by unutbu on 2009-01-01
You could use remastersys to make a LiveCD or LiveDVD of your system:

remastersys homepage:
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

A nice howto tutorial:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by thomas228 on 2009-01-01
> **unutbu said:**
> You could use remastersys to make a LiveCD or LiveDVD of your system:

remastersys homepage:
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

A nice howto tutorial:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Would this work with making a Liveusb??? (2 - 8GB)

Thanks 

Tom

---

### Post by unutbu on 2009-01-01
I haven't tried this myself, but according to wikipedia:

```
It is a very useful and easy way to create a customized Live CD/DVD version of Ubuntu, once the system is installed and configured with programs, updates, etc... the user just has to:

   1. Download and install the latest version of Remastersys from: http://remastersys.klikit-linux.com/repository/remastersys/
   2. Open the program (a shortcut is created on the desktop) and then choose the dist or backup option, and then the iso of the Live CD will be automatically created.

**The resulting iso can also be installed on a USB pendrive, creating a Live USB distro**, using either a command-line approach[1] or a graphical tool such as UNetbootin.
```

See [http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by klein de usa on 2009-01-02
hi 
first off i do have high speed, but it is caped at 500mb in 24 hours, (hughes.net)
remastersys looks like it will work i will have to try it, thank you all for your time!

---

