---
title: "Install Screen res problems..."
date: 2009-12-28
forum: New to Ubuntu
---

### Post by BostonAMC on 2009-12-28
Alright, I've been trying to search for my problem and all I've come up with is unrelated stuff so I'm sorry if this is a repost.

So I'm re-installing ubuntu 9.10 after adding a few more drives and going through the issues installing windows after ubuntu and writing over grub (oops)...

The screen resolution looks like it's lower than 800x600... I can't see the partition selector and I'm worried about where I'll install if I just TAB ENTER ahead...

is there anyway to change the screen resolution when you're in live CD install mode?

It did this before but the machine was simpler then so TAB ENTER worked fine...

Thanks!

---

### Post by sirgogo on 2009-12-28
When theres a will, theres a way (in Linux).

1. Boot from the live cd.
2. Go to Places-->(Drive) to mount your hard drive.
3. Open a terminal from Applications-->Accessories-->Terminal
4. Type ```
cd /
```
5. ```
cd media
```
6. ```
ls
```
7. ```
cd Drive
``` Drive=the drive you mounted. It should look like a folder, its listed after you enter step 6.
8. ```
sudo nano etc/x11/xorg.conf
```. You can also use gedit, which is a non-terminal text editor. If you want to do that, type ```
sudo gedit etc/x11/xorg.conf
```
9. Edit the xorg.conf as you would normally (if you don't know how,[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973))

Cheers, let us know how it goes.

Edit: I guess I didn't read it clearly enough. I'm not sure where the xorg is stored when running the live cd. You may want to just try
```
sudo /etc/x11/xorg.conf
```
without navigating to any given drive. Hopefully that will work.

Or ```
sudo dpkg-reconfigure xserver-xorg
```

Hope it works.

---

