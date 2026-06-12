---
title: "Partition emergency"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-21
I dont see itim at the partition part of insall from live CD. If i click manual nothing happens... If i go "guided resizebSCSl1 (0,0,0), partition #1 (sda) and use free space"

Or manual??

If i click manual nothing appears... Should i just use the guidednresize. It gives windows 30g out og 320 and ubuntu 89%. Helpzzz. Im waiting for answers before anyhing..

---

### Post by taurus on 2009-03-21
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Skol312000 on 2009-03-21
I did a fresh install. And im at the "prepare dik space" part

---

### Post by SuperSonic4 on 2009-03-21
sudo fdisk -l will show what hard drives you have that ubuntu recongnises

---

### Post by ivanvajar on 2009-03-21
Did you create a partition for Linux from LiveCD?

---

### Post by Skol312000 on 2009-03-21
I just nees to choose right now so i can complete installation from live cd.. P

---

### Post by Skol312000 on 2009-03-21
I didnt choose yet... My options are in my first post

---

### Post by Therion on 2009-03-21
Well it depends.  Do you WANT your Windows install to have 30GB and your Ubuntu install to have 89% of your drive so you can dual-boot?  Do you want Ubuntu as your sole OS on the drive...  Or what??

What I mean is, you're not telling us what you want as the final product so it's hard to tell you how to proceed.

---

### Post by ivanvajar on 2009-03-21
You need to shrink your Windows partition (to approximately 50GB, wich leaves yo 20 GB free on it) and create 1 EXT3 and 1swap partition (swap size = RAM size). During installation go to manual and select your ext3 partition and give it mountpoint'/'. You'll see. It's as simple as that. :-)

---

### Post by Skol312000 on 2009-03-21
I chose for windows to have 40 gb and thrrest to ubuntu...
I hate how i have to instal all the updates 277 of tem again...

---

### Post by ivanvajar on 2009-03-21
Be careful with updates. Sometimes they mess things up a bit.

---

### Post by Skol312000 on 2009-03-21
I have to get thrm in order to be up to date tho right?   Also... How do i get the cool codecs thogh sudo?

---

### Post by ivanvajar on 2009-03-21
Codecs via Terminal:

32-Bit Ubuntu:

> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

64-Bit Ubuntu:

> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar

This should install complete multimedia support.

---

### Post by Skol312000 on 2009-03-21
Awesome. Thanks.... How do i make sure that the updates wont mess my thingsnup?

---

### Post by ivanvajar on 2009-03-21
Run without updates for a while and see if you need them at all. Hang around forum to see if there are problems after updating system. :-)

---

### Post by Skol312000 on 2009-03-21
i got 277...........u sure i dont need at least some of them...are you rocking it without updates?

---

### Post by ivanvajar on 2009-03-21
I run Ubuntu 8.04 without updating for 4 months. It never failed. :-)

---

### Post by carml on 2009-03-21
I recommend to install the update,but first finish your installation and see if all is well. :)

---

### Post by Skol312000 on 2009-03-21
all was good..i had a little problem with the internet conncetions after i installed updates..but all of it good now..thanks you all for the help

---

### Post by Old_Grey_Wolf on 2009-03-21
I agree with carml. Finish the installation, then install the updates. 

The only time I have had problems with updates has been when the kernel was updated. And only when I had to install proprietary video or network card drivers for hardware the was not Linux friendly. 

Fortunately, the boot menu allows you to boot an older kernel when such problems arise.

Edit: I see you got it working. Simultaneous posts. hehe.

---

