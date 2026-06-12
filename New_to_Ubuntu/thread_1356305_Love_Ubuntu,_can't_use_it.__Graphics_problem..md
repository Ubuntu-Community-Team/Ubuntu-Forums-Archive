---
title: "Love Ubuntu, can't use it.  Graphics problem."
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Boise Jim on 2009-12-15
Installed Ubuntu 9.10 (first time user) on a rebuild computer that I want to use for an HTPC, and I would like to not use Windows.  My problem is that I get a bunch of horizontal black lines and it makes the display unusable.  I've downloaded all the updates and updated the video driver (using ATI Radeon HD 3200), but nothing is helping.  
Sadly, I have no problems when I'm using XP.

Any ideas?

Thanks,
Jim

---

### Post by Diametric on 2009-12-15
Could you post a complete list of your hardware specs?

---

### Post by wojox on 2009-12-15
Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by anewguy on 2009-12-15
Is the "bad" display after you log in or just there the entire time Ubuntu is booting as well?  If only after you log in, please do the following:

(1) hold down the ctrl and alt keys and press F1.  This should give you a text-based log in. 

(2) type:

cat /var/log/Xorg.0.log <press enter> (I *think* that's the name - let me know if it fails as I'm currently not at my Linux box).

Scroll through the output and see if there are any error messages (may be something like 3 or 4 "*"'s with it) and post them back here.

(3) type: 

lspci | grep VGA <press enter) That's a piping symbol - on my keyboard it is above the "\" key.  Post the output back here as well.


Thanks
Dave :)

---

### Post by lrcaballero on 2009-12-15
go to system/administration/hardware drivers and see if there is any drivers available for your video card, if there is install it and restart your computer. Hopefully this will work.

Good Luck

Luis

---

### Post by greg963 on 2009-12-16
I would recommend using the radeonhd driver for a radeon 3200

1. When you get the black lines press Ctr+Alt+F1
2. Login using your username and password
3. at the prompt type: 
```

sudo apt-get install radeonhd
sudo dpkg-reconfigure -phigh xserver-xorg

```

next edit the xorg.conf file
```

sudo nano /etc/X11/xorg.conf

```
find the line that contains the word "Driver"
```

Driver "ati" ##note yours may not read ati
and change to
Driver "radeonhd"

```
press Ctrl+X to exit and choose yes to save
last
```

sudo restart gdm

```

---

