---
title: "Realtek 8188SU driver stops working each time I reboot"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Andreg69 on 2010-11-15
Hi, I'm new to Ubuntu (maverick) so please excuse extreme ignorance.
 
My Realtek 8188SU wireless USB dongle works after I go through the process of installing the driver that I downloaded. The problem is I have to redo this process every time I reboot:
 
make
./clean
insmod 8172u.ko
 
Could someone explain modprobe to me as I think I need to do that...?
 
It would also be interesting to know what 'make', 'clean' and 'insmod' do - could you direct me to a good reference source? I run these with the sudo prefix - not sure if thats strictly necessary.
 
Thanks
A
 
IBM ThinkCentre 2.4GHz P4, 1GB RAM, 1TB SATA HD, Logitech wireless keyboard&mouse, Realtek 8188SU wireless dongle

---

### Post by ibizatunes on 2010-11-15
[http://ubuntuforums.org/showthread.php?t=1573669](http://ubuntuforums.org/showthread.php?t=1573669) there is a how to there

---

### Post by Andreg69 on 2010-11-15
Yes thanks I follow that thread every time I reboot.  It doesnt explain the syntax to modprobe the driver.

---

### Post by Andreg69 on 2010-11-15
Can anyone help with this?  How do you modprobe a driver so it is reused each time ubuntu boots?

---

### Post by Andreg69 on 2010-11-16
Well I didn't get any help, and was very close to giving up and going back to Windows, but I finally got the driver to persist after a reboot.  Chilli555's advice on this thread helped:  [http://ubuntuforums.org/showthread.php?t=1425697](http://ubuntuforums.org/showthread.php?t=1425697)

I did lots of trial and (mostly) error changes but the thing that finally got it working was blacklisting the old driver module - which previously kept appearing in the lsmod list:

[sudo gedit /etc/modprobe.d/blacklist]    

Add an extra line to the file (for me the file was blank to start with): 
blacklist r8192s_usb    

Also I did this (not sure why!):     
[sudo mv /etc/modprobe.d/blacklist  /etc/modprobe.d/blacklist.conf]

---

### Post by Tangerine Tom on 2010-12-02
Hey Andreg69,
 
Thanks for posting this.  I'm a complete newbie to Ubuntu (or Linux for that matter) so am still very much trying to get my head around the command prompt interface let along resolving my wireless USB problems.
 
I too have got a Realtek 8188S device which isn't working.  I'll let you know how I get on trying to fix it but rest assured your efforts aren't in vain :)
 
TT

---

### Post by Tangerine Tom on 2010-12-04
OK I cracked it, plus it's working (so far) when I reboot.  I followed a miriad of instructions from a few different blog pages.  I followed through what chilli555 said but because I was on 10.10 I didn't actually need to do so (drivers were already installed).

The main thing that was making things slow was the firmware configuration.  It was as if Ubuntu knew the device was plugged in, it just didn't know what to do with it. 

In addition, I actually cleared my blacklist file.  I'm not sure whether that had any effect, I was trying so many things today that I lost track a little as to what was making me progress and what was having no effect at all.

All I know for sure is that it's working and that I'm very relieved.  That was my first venture into configuring anything on Linux.

Thanks to everyone who posts on here, your help/knowledge is invaluable.

---

