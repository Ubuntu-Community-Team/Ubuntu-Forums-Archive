---
title: "startup script?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Aisthesis on 2010-05-25
how do i as completely new to linux set up a startup script in init.d that enables the driver for my wireless that i get from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 
also, these drivers are tar files. if i just put them somewhere and type tar -xf /path/filename, will the files be extracted automatically to the proper location?
 
this is a continuation from here: [http://ubuntuforums.org/showthread.php?t=1492033&page=2](http://ubuntuforums.org/showthread.php?t=1492033&page=2) but the responses seem to have dried up, and my wireless still isn't working.

---

### Post by isaacj87 on 2010-05-25
> **Aisthesis said:**
> how do i as completely new to linux set up a startup script in init.d that enables the driver for my wireless that i get from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 
also, these drivers are tar files. if i just put them somewhere and type tar -xf /path/filename, will the files be extracted automatically to the proper location?
 
this is a continuation from here: [http://ubuntuforums.org/showthread.php?t=1492033&page=2](http://ubuntuforums.org/showthread.php?t=1492033&page=2) but the responses seem to have dried up, and my wireless still isn't working.

Hello there,

I've actually had to use those same drivers before with Opensuse 11.2. However, I think you're making this more complicated then it needs to be! I read the other thread you started and I assume you figured out what version of Ubuntu you installed, correct? If so, I can help you install this driver.

There are two routes you could with this. 

1) **Use the "Hardware Drivers" utility located in System -> Administration**.
I'm assuming you're using Ubuntu 10.04. This would be the path of least resistance. Just remember the choose the "STA" driver and not "B43" This seems to confuse Ubuntu if you choose the incorrect one. 

**OR**

2) You can do it **the long way**. The tar you downloaded contains the drivers, however, you have to compile them and will be forced to repeat the process every time there is a kernel update. But if you choose to do it this way, here's how (this worked on Opensuse and should on Ubuntu):

I'm summarizing what's written from the official README for the drivers located here: [http://www.broadcom.com/docs/linux_sta/README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt") and I'm assuming you have an internet connection and that you've downloaded the right version for you comp. I'm also assuming that you've got a handle on entering commands as you seem to already to possess some computer knowledge. If my instructions come off as patronizing, I apologize. I want to be thorough. 

A) You need to prepare your comp for compiling the driver. Open up a terminal window, copy and paste this:

```
apt-get install build-essential linux-headers-generic

```

then this,

```
apt-get build-dep linux
```

Let this finish.

B) Make a directory and extract the files needed to compile. (This partly answers one of your questions regarding extracting the tar):

```
mkdir hybrid_wl
```
```
cd hybrid_wl
```

32 bit:
```
tar xzf <path>/hybrid-portsrc.tar
```

**OR** if you have,

64 bit:
```
tar xzf <path>/hybrid-portsrc-x86_64.tar.gz
```

Now it's time to compile:

```
make clean
```
```
make
```

Let's install!

The "**path-to-prev-driver**" is the kernel version you have installed located in /lib/modules/KERNEL-VERSION/net/wireless 

To determine what kernel you're running, run this command:

```
uname -a
```

The version I'm running is 2.6.31-10-rt. Therefore, the "path-to-prev-driver" for me is located in /lib/modules/2.6.31-10-rt/net/wireless. However, yours will more than likely be different. Now, that you've figured out what version of the kernel you're running, carry on:

```
rmmod wl
```
```
cp wl.ko <**path-to-prev-driver**>/wl.ko
```
```
depmod
```
```
modprobe wl
```

Now remove the other modules so they don't interfere:

```
rmmod b43
```
```
rmmod ssb
```

Now blacklist them so they don't startup on boot:

```
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
```

This should do it. Do a restart and the drivers should start up. If you have any questions, refer back to the README I posted towards the top.

---

### Post by Aisthesis on 2010-05-25
thanks for your help. yes, as i said originally, i'm using ubuntu 10.04. there was never any doubt about that, but rather whether or not 64-bit install. i'm really of the opinion that it is a 64-bit install on my Intel Core 2 Duo (x86_64 seems to always show up when i look for drivers appropriate to my hardware configuration--which i've been doing a lot of the last day or so ...)
 
anyhow, as to the easy way: when i go to system > administration > hardware drivers
i just get an error box saying: "No proprietary drivers are in use on this system."
 
There's never an option to enter STA or B43.
 
So, I'll try doing it the long way, as you outlined.

---

### Post by Aisthesis on 2010-05-25
sigh... ok, on part A), I typed actually
 
sudo apt-get install build-essential linux-headers-generic
 
because it has to be run with admin privileges, and my install only allows them using sudo (root being encrypted). anyhow, that started to run when i entered my password, but the result was this:
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential
 
i didn't proceed further because i figured the whole point was to get that package installed... :(
 
btw, my internet setup is this: i can download only through my windows computer and of course can then enter commands as long as i know where to enter them. but to transfer over to the ubuntu machine, i have to use either flash--or, if it's something bit, i can make an image of a dvd.
 
from what you're saying, i'm wondering whether it wouldn't be a good idea to try to find another copy of ubuntu 10.04 and make my own dvd. the dvd i'm using only has 699 MB written to it, and i'm beginning to wonder if there aren't some drivers missing that would make it much easier to get hooked up. i'd REALLY like to use your "path of least resistance" rather than going through all this stuff--although i guess it does have the advantage that i'm getting a crash course in unix command line... :)

---

### Post by cariboo on 2010-05-25
I use the same driver for my netbook, you don't have to install it, go to System->Administration->Hardware Drivers, and select it for installation, you have to have a network cable connected to do it. If you don't have a network connection you can download bcmwl-kernel-source form [here]("http://packages.ubuntu.com/search?keywords=bcmwl&searchon=names&suite=lucid&section=all") and use gdebi to install it, once you have downloaded the package just double click the package and follow the instructions.

---

### Post by isaacj87 on 2010-05-25
> **Aisthesis said:**
> sigh... ok, on part A), I typed actually
 
sudo apt-get install build-essential linux-headers-generic
 
because it has to be run with admin privileges, and my install only allows them using sudo (root being encrypted). anyhow, that started to run when i entered my password, but the result was this:
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential
 
i didn't proceed further because i figured the whole point was to get that package installed... :(
 
btw, my internet setup is this: i can download only through my windows computer and of course can then enter commands as long as i know where to enter them. but to transfer over to the ubuntu machine, i have to use either flash--or, if it's something bit, i can make an image of a dvd.
 
from what you're saying, i'm wondering whether it wouldn't be a good idea to try to find another copy of ubuntu 10.04 and make my own dvd. the dvd i'm using only has 699 MB written to it, and i'm beginning to wonder if there aren't some drivers missing that would make it much easier to get hooked up. i'd REALLY like to use your "path of least resistance" rather than going through all this stuff--although i guess it does have the advantage that i'm getting a crash course in unix command line... :)

Ahh. Okay. Believe it or not, we're getting somewhere. I didn't realize you had no internet connection on your *Ubuntu* computer. This is why you're not getting any available drivers in "Hardware Drivers" nor anything when you try the "long way." However, all hope is not lost.

Can you not plug your Ubuntu computer into a wired connection? If so, you should be able to go the "path of least resistance."

**EDIT**: cariboo907 found what I was trying to find. Just install the deb package he/she listed!

---

### Post by derrick81787 on 2010-05-25
I use this driver too, and the Restricted Drivers Manager handles it just fine for me.  I don't remember what it says when you first open it and the drivers aren't yet activated, but it might be the "No proprietary drivers currently in use" message that you said you got.  That's not an error message, but is just stating that you aren't using any proprietary drivers at the moment (which is why your wireless isn't working).

I'm away from home right now and so can't go through the steps on my own machine, but somewhere in the Restricted Drivers Manager should be an option for activating this driver.

The steps you should have to follow should be something like what is found [here]("http://www.ghacks.net/2009/04/15/using-proprietary-drivers-in-ubuntu/"), although that post is over a year old.  If that is what you did and it is still not working, then I don't know if I can help at least until I get back to my Ubuntu machine.

- Derrick

---

### Post by Aisthesis on 2010-05-25
in the meantime, i've installed fedora and, while having similar problems, am at least trying to see that through far enough to give it a shot at working. if it's not working by tomorrow (and i'm pessimistic, i'll have to admit), i'll repost here-- or of course if i get it working whenever.
 
in the meantime, i'll check out the links you guys gave.
 
and one thing for the record and to be completely clear: on the ubuntu/fedora machine, i can get no internet connection of any kind at all, not wired, not wireless. if i had wired, then i obviously wouldn't be going to the trouble of transferring constantly through flash from one machine to the other.
 
a wired connection is not available at my apartment, nor do i have the cable, and i'm not at the point yet of packing up the machine, buying an ethernet cable and then finding an appropriate spot to connect to.

---

### Post by Aisthesis on 2010-05-26
ok, i downloaded the bcmwl-kernel-source ... file linked in cariboo907's post (#5), then put it on my flash, transferred to ubuntu machine and double clicked.
 
a window opens with the title Package Installer bcmwl-kernel-source.
 
but under status there's the message in red 'Error: Dependency is not satisfiable: dkms'
 
and the 'Install Package' button on the upper right in that window is grayed out.
 
i actually feel like this is progress, as it WOULD install if only i had dkms (?). any ideas on how to fix this problem?

---

### Post by isaacj87 on 2010-05-26
> **Aisthesis said:**
> ok, i downloaded the bcmwl-kernel-source ... file linked in cariboo907's post (#5), then put it on my flash, transferred to ubuntu machine and double clicked.
 
a window opens with the title Package Installer bcmwl-kernel-source.
 
but under status there's the message in red 'Error: Dependency is not satisfiable: dkms'
 
and the 'Install Package' button on the upper right in that window is grayed out.
 
i actually feel like this is progress, as it WOULD install if only i had dkms (?). any ideas on how to fix this problem?

Aisthesis,

Try this: [http://packages.ubuntu.com/search?suite=lucid&section=all&arch=any&searchon=names&keywords=dkms](http://packages.ubuntu.com/search?suite=lucid&section=all&arch=any&searchon=names&keywords=dkms)

It has actually become a lot easier to installed 3rd-party drivers on Ubuntu, however, it's difficult to do so without a internet connection (a.k.a wired connection). It's difficult, but not impossible.

---

### Post by Aisthesis on 2010-05-26
well, i'm finally up and running with fedora x86_64. basically, i decided to keep trying with both and use the one where i got set up first. thanks for all the help!

---

