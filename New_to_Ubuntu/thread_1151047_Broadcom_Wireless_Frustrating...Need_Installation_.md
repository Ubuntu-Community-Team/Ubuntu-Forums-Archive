---
title: "Broadcom Wireless Frustrating...Need Installation help"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by noobie mcnoob on 2009-05-06
Hello all.  I am brand new to Linux having been a Windows Guy for a while.  I have decided to branch out a bit and am currently Using Hardy on a Dell Inspiron 1521.  The issue is that I cannot for the life of me figure out how to get the wireless network setup.  Thus far everything has been easy, but I've spent (literally) 5 hours browsing web pages and reading posts and I just cannot get this wireless network setup.  The furthest I got was with ndiswrapper where I had a driver installed, but I could not get connected.  At one point I had the network present and when I tried to connect I kept having to enter teh WPA2 key, but could never actually get an IP. At this point I think I may have to start from scratch and undo what I've done in order to move forward. I'm so lost.  HELP!

---

### Post by Law506 on 2009-05-06
Its been awhile since I have messed with this, but I believe you are needing bw43-fwcutter to be installed on your system.  Buddy had a dell that had broadcom in it and he grabbed that (bw43-fwcutter) and had some luck.  Searching for it in 9.04 and its not coming up in Synaptic.

---

### Post by General-Gouda on 2009-05-06
> **noobie mcnoob said:**
> Hello all.  I am brand new to Linux having been a Windows Guy for a while.  I have decided to branch out a bit and am currently Using Hardy on a Dell Inspiron 1521.  The issue is that I cannot for the life of me figure out how to get the wireless network setup.  Thus far everything has been easy, but I've spent (literally) 5 hours browsing web pages and reading posts and I just cannot get this wireless network setup.  The furthest I got was with ndiswrapper where I had a driver installed, but I could not get connected.  At one point I had the network present and when I tried to connect I kept having to enter teh WPA2 key, but could never actually get an IP. At this point I think I may have to start from scratch and undo what I've done in order to move forward. I'm so lost.  HELP!

The hardware monitor detected my Dell Latitude D600's broadcom wireless card after I ran a few updates through it.  Try hooking it up to a physical network connection, run through some of the automatic updates, restart your computer and see if it finds any proprietary drivers for it.

---

### Post by noobie mcnoob on 2009-05-06
I tried this and it says extracting and does a whole lot, and then there doesn't appear to be any change that I can see.  AT this point i don't even have the option to select or configure a wireless network.

---

### Post by albinootje on 2009-05-06
> **noobie mcnoob said:**
> Using Hardy on a Dell Inspiron 1521. 

Did you check this ? Instructions for Hardy on a 1521 :
[http://snackfin.com/2008/06/ubuntu-804-lts-on-dell-inspiro.html](http://snackfin.com/2008/06/ubuntu-804-lts-on-dell-inspiro.html)

And did you try a live session of Ubuntu Jaunty ?

---

### Post by noobie mcnoob on 2009-05-06
I checked for updates and restarted multiple times, but there's no new updates and still no wireless

---

### Post by noobie mcnoob on 2009-05-06
I haven't tried the repository thing yet.  Let me see and I'll get back to ya...Gimmie like 10 min

---

### Post by albinootje on 2009-05-06
> **Law506 said:**
> I believe you are needing bw43-fwcutter to be installed on your system.

See here (two choices by the way..) :
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fwcutter](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fwcutter)

---

### Post by acimmarusti on 2009-05-06
Please open up a gnome terminal and type the following:

```

lspci -v | grep Network

```

Post the output, so we can see what wireless pci card you are using. Then we can plan how to solve this

---

### Post by noobie mcnoob on 2009-05-06
you guys are awesome!! I had to enable third party software updates in the repository section and then restart the machine.  Once I had done this, and it took a while, the wireless jsut started working.  Thanks so much!!!

---

### Post by noobie mcnoob on 2009-05-06
If there's a mod here they may want to close this thread.

---

### Post by albinootje on 2009-05-06
> **noobie mcnoob said:**
>  Once I had done this, and it took a while, the wireless jsut started working.

Cool, congrats! :)

---

