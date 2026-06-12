---
title: "X server will not start?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by merc1973 on 2010-05-23
Hi, I'm running Linux Mint 8 x86 on my ancient laptop Dell c840 (2.4 GHz P4, Geforce 440 Go, 1.5 GB ram, 60 GB HDD) and I am having problems after Installing and Uninstalling "Startupmanager" (to customize login splash screens) which apparently rewrote my Xorg files.... yay....  :(   So after some reconfiguring and adding appropriate lines to get it working ok, I notice upon restart X server does not start and I can only run in "low resolution" one time for Ubuntu...  To get it working I have to type in terminal:

```
sudo nvidia-xconfig --add-argb-glx-visuals
``` and 
```
sudo /etc/init.d/gdm restart
```
How can I have X server start upon rebooting?

---

### Post by wojox on 2010-05-23
Try this [http://newyork.ubuntuforums.org/showpost.php?p=9277270&postcount=5](http://newyork.ubuntuforums.org/showpost.php?p=9277270&postcount=5)

---

### Post by merc1973 on 2010-05-24
> **wojox said:**
> Try this [http://newyork.ubuntuforums.org/showpost.php?p=9277270&postcount=5](http://newyork.ubuntuforums.org/showpost.php?p=9277270&postcount=5)


What thread was this from or letmem rephrase, what is the goal of these steps?  Is this "new" xorg config going to change my current settings? Thanks.

---

### Post by merc1973 on 2010-05-27
Did not work, but thanks.

---

### Post by skippuff54 on 2010-05-27
I had some issues after upgrading, and one of the first steps I took was to manually upgrade GRUB boot loader to GRUB2. I am trying to remember what exactly I did after that, but I have an Intel graphics card anyways. 

You might need to mess with some settings in /etc/default/grub

Edit: Maybe this thread would give you an idea...Check out the solution provided by TheRawGod:

[http://swiss.ubuntuforums.org/showthread.php?t=1470822]("http://swiss.ubuntuforums.org/showthread.php?t=1470822")

---

