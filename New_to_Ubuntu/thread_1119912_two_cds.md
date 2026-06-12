---
title: "two cds"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by wavector on 2009-04-08
I downloaded Ubuntu 8.10 but I only have 650 mb cds to work with and no other medium. I don't know how to create a partition to go that route. I'm green. Is there a way to write Ubuntu in 2 - 650 mb cds?

---

### Post by Jakey_TheSnake on 2009-04-08
Are you dual booting with a windows partition? If so, you could use Wubi - the Windows based Ubuntu installer. 

Do you have access to a machine that runs Ubuntu, like one of your friends? If so, you can give them a 1GB USB-drive, and they will be able to create a Live-USB for you, that is the same as the disk.

---

### Post by LowSky on 2009-04-08
The server edition will fit onto a 650MB CD, but using that will  require exra steps to install to get a destop enviroment

otherwise use the option for them to ship you a free CD
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by cariboo on 2009-04-08
You can't split the iso between two cd's but if you're willing to wait a couple of weeks you can get a free cd shipped to you. Check out [Shipit]("http://shipit.ubuntu.com/").

Jim

---

### Post by wavector on 2009-04-08
I tried to see about a free shipped copy, but it says they are away for little while. Anyway. If 690+ mb will fit on 650 mb cd then how do I do that? I may try to dual boot RHL 9.0, which I have installed now and am using. WinXP crashed for the last time yesterday in my life, and I had a sealed RHL 9.0 and installed it. I'm green to all of this. I'm a ex-Wimpdows idiot.

---

### Post by LowSky on 2009-04-08
the Xubuntu version of Ubuntu is only 544 MB, which will fit to one disc
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/xubuntu-8.04.1-desktop-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/xubuntu-8.04.1-desktop-i386.iso)

once you install Xubuntu open a terminal and type
```
sudo apt-get install ubuntu-desktop
```

this will install the Gnome desktop that Ubuntu uses 
very simple upgrade over the internet

---

### Post by lisati on 2009-04-08
> **wavector said:**
> If 690+ mb will fit on 650 mb cd then how do I do that? 
I've heard of some software having the ability to squeeze a little extra on a CD but would advise against it: there's a risk of data errors, which probably wouldn't be acceptable for files that would potentially be used to install an OS.

Your best bet would be either the free CD option or wait until you have a larger capacity blank disk available to use.

---

### Post by matrixblue on 2009-04-08
Or you can use unetbootin and create a live-usb flash drive and install ubuntu from that. That is is you have a 1GB or More flash drive.

Otherwise download the server edition and run sudo apt-get install ubuntu-desktop

---

