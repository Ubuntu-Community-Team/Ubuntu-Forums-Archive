---
title: "only background after log in"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by gcampbell86 on 2011-01-21
I have recently installed Xubuntu 10.04 onto an old laptop, it had Ubuntu 9.04, but thought it would help if I put Xubuntu on it as it hasnt got a great amount of RAM.

Anyway, I installed it fine, then installed all the upgrades in the download manager.  Now after logging in, I just get the background and nothing else and it stays like that forever.

Is there anyway of getting past this?

---

### Post by Rubi1200 on 2011-01-21
Hi and welcome to the forums :)

How much RAM and what graphics card are we talking about here?

Two options to try:

1. freezes/hangs after login:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials)

2. reconfigure the graphics. You need to boot into recovery mode, drop to a command shell and run these commands:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

---

### Post by gcampbell86 on 2011-01-21
Thanks for that, I will give it a try to see if it works.

Its an old Dell Inspiron 1200, with 256mb and the integrated graphics card.

---

### Post by Rex Bouwense on 2011-01-21
Something that you might consider is adding another 256 RAM chip.  I have Ubuntu 10.04 running on an old Dell Inspiron 1000 and the only modification I did was add more memory.  It is running fine and has been since last April (so far.)

---

### Post by verymadpip on 2011-01-21
Lubuntu will run better than Xubuntu with 256Mb RAM.  It worked for me.  I have added more RAM to my machine since & I still run Lubuntu.

[http://lubuntu.net/blog/lubuntu-1010-released](http://lubuntu.net/blog/lubuntu-1010-released)

---

### Post by hansolo4949 on 2011-01-21
Perhaps you accidentally (or the system did) set your session to the "user defined session", which I have found just gives you a blank screen. When the computers starts up, in the login menu, on the bottom toolbar, there should be a drop-down menu that says "session" or something like that. Just select "Xubuntu session" and you should be good to go! if that doesn't work, you might have a broken package. Press ctrl-alt F1, to drop down to the terminal, then type: sudo apt-get install --fix-broken.(without the period). Then, type sudo reboot, to reboot. That might work. If not...it is probably a problem with the specs on your computer. I have subscribed to this thread, so I will be able to help if none of that works!

---

### Post by verymadpip on 2011-01-21
You could try:

```
xfce4-panel &
```

in a terminal, if you can fire a terminal up that is.

---

