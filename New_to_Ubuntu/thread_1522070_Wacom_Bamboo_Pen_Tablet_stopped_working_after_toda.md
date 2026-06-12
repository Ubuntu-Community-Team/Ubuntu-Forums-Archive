---
title: "Wacom Bamboo Pen Tablet stopped working after today's kernel update. Here's a fix."
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-07-01
Yeah so my Wacom Pen stopped working right after I did the update to the kernel on Lucid. So I went through the same process I did to get them installed in the first place and now it's working again! Here's what I did, oh and credit goes to Frank Groeneveld on his weblog, I just updated the commands with the newest drivers.

Frank's weblog:
[http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

```

sudo apt-get install build-essential libx11-dev libxi-dev  x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

``````

 wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-4.tar.bz2]("http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2")

``````

 tar -xf linuxwacom-0.8.8-4.tar.bz2

``````

cd linuxwacom-0.8.8-4

``````

./configure --enable-wacom

``````

cd src/2.6.30/

``````

make

``````

sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/

```If memory serves me correct you might just get an error from this, ignore it and just enter the next command.
```

 sudo rmmod wacom

``````

 sudo modprobe wacom

```

The tablet should work now. You can also add the module name to  /etc/modules to automatically load it on boot. I haven't rebooted yet so I don't know if this will be an issue for me yet, but it wasn't a problem the last time I did it. Oh I won't go through activating the pressure detection, I never did that so I'm not sure what works.

---

### Post by Legendary_Bibo on 2010-07-02
Oh look I'm nice, and I just learned how to make shell scripts. It's that freaking easy? Okay so I turned it into a shell script which all you do is execute in a terminal. ;)
It'll do everything for you. Except enter your password. :P
I also removed the sudo rmmod wacom command because it didn't seem to do anything.

---

### Post by jferna57 on 2010-07-02
Thank you very much.

JK

---

