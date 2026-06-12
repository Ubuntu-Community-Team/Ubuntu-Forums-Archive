---
title: "Issues with Asus Eee"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by zurrado on 2009-05-13
Hello everybody!

I have just installed Ubuntu on my new ASUS EEE 1000HE laptop and i am very disappointed.

1st thing is that it seems like this system is really slow and every program takes a couple of seconds to open unlike windows where it just opens itself right away. It seems clumsy?

2nd thing is that it disconnects from the wireless connection every 10 minute which it doesnt in Windows

I installed it with the Wubi installer, could this have anything to say that it is so slow?

Is this the thing with linux/ubuntu or is it something wrong?

When i tried it out I thought that it was going to be smooth, quick, easy and so on, but it looks like windows is reaally way ahead, or is it something that i have missed?

---

### Post by HeirPixel on 2009-05-13
Well, you have made a few comments in your post that point to some issues:
[LIST]
[*]You're using an Asus Eee system that runs on an Atom processor. These are not particularly known for high speed and running multiple heavy threads.
[*]You're using Wubi, so you're running one entire OS (Ubuntu) *inside* another (Windows). This will often slow down your applications, and again, that Atom proc really isn't designed for that sort of load.
[*]Because you're using Wubi, certain drivers can have trouble carrying over to Ubuntu. It's the same sort of issue the other way around (e.g. running Windows within Parallels).
[/LIST]
Props on giving Linux a try, and especially on taking the time to join our forum for more info. Many people would simply give up and turn around without even trying!

---

### Post by LowSky on 2009-05-13
Ubuntu runs fine on my netbook. But then agian I didn't use WUBI

---

### Post by ugm6hr on 2009-05-13
There are EEE-specific versions available.

9.04 netbook remix is supposed to work well too: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

If you are serious about trying Ubuntu, try installing it to an SD card properly.  Wubi has unusual idiosyncrasies which may be interfering; there should certainly be no issue with wifi.

I use Ubuntu 9.04 NBR on my Dell Mini 9, and find it very quick.  While I have never used XP on this device, I would be surprised if it was quicker.

One thing I will say is that the Windows desktop and applications open instantaneously, but they are not truly usable for a few seconds.  On Ubuntu, you do get a loading icon for a few seconds, but the application is generally usable immediately.

If you like the general feel of Ubuntu, consider giving it another go.  If you prefer XP, just remove your Wubi install.

---

### Post by zurrado on 2009-05-13
Oh so there may have something to do with Wubi. Almost thought so but I wasnt sure. So maybe I should try to install it from some kind of USB thing...

Do anyone know if it is possible to install it from a Western Digital USB disc, (without need of power cables) ? It is the only external memory I have..

I am really ready to try it out actually. Just because that there is nothing that I hate more when you have to format your disc to get it fast again. 

Any other suggestions?

Are there any other good reason to change from XP to Ubuntu?

---

### Post by ugm6hr on 2009-05-13
Do you want to install from the WD USB drive, or on to the drive?

Do you have any other data on the drive?

I am astounded a netbook owner does not have any USB flash drives or SD cards!

---

### Post by zurrado on 2009-05-13
I want to install FROM the wd drive.

Haha I know, just lost everything when i changed apartment ;P

---

### Post by ugm6hr on 2009-05-13
> **zurrado said:**
> I want to install FROM the wd drive.

Unless it is blank, I can't think of an easy way.

---

### Post by Nostalos on 2009-05-13
Unetbootin will allow you to install to an external drive as well as a USB stick.  

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  

It doesn't have to be empty, but it does have to be formatted FAT32.    If not viable,  run to the corner and grab a cheap 1GB thumb drive.  Can pick on up for pocket change.

9.04 runs rock solid on my Asus 900A even with the very slow SSD it has.

---

### Post by Jazzy_Jeff on 2009-05-13
> **zurrado said:**
> 
Are there any other good reason to change from XP to Ubuntu?

Lots of reasons. No viruses for one. Then there are also thousands of free software you can play with to see what you like.

---

### Post by blueridgedog on 2009-05-13
I have the eee PC 1000 and the 9.04 netbook remix installed and operated perfectly.  The only tweaks were getting the camera to work.  It is a great OS for that platform and I find it more responsive than windows.

---

### Post by rustutzman on 2009-05-14
I installed 9.04 full on two Asus 1000he's and didn't have any problems. First thing to do after that is to grab the kernel from [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) With that installed everything worked. 

I did have to do one extra step to get my Microsoft Bluetooth 5000 mouse working. I had to install bluez-compat and then in a terminal run sudo hidd --search. With that the mouse was paired and works great!

The machine is surprisingly snappy. I did install a 2GB chip before I even turned the machines on though. After a full day of use I'm very happy with both the Asus 1000he and Ubuntu 9.04

Russ

---

### Post by bennachie on 2009-05-14
I run Ubuntu 9.04 on my eeePC 701 4G, and have done since it was made available in Beta form. It has been entirely reliable, and is, at least subjectively, more responsive than Windows Vista on my dual-core desktop (and a heap less trouble to keep going). Everything works well (only the web-cam required a bit of "adjustment").

In my experience, Windows XP puts quite a strain on the resources of the average Netbook, and has minimal spare capacity to run Ubuntu under Wubi as well. The most sensible approach, accepting that you are probably reluctant to junk XP, for which you may well have paid a substantial premium, would be to install Ubuntu on an SD card (a 4G one will do nicely, since you will be able to access data from your existing NTFS partitions on the hard disk) and try it out in that mode for a while. It seems a bit of a waste to use your external hard disk for that purpose, but is certainly possible.

---

### Post by enchantedsky on 2009-05-16
> **rustutzman said:**
> I installed 9.04 full on two Asus 1000he's and didn't have any problems. First thing to do after that is to grab the kernel from [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) With that installed everything worked. 

I did have to do one extra step to get my Microsoft Bluetooth 5000 mouse working. I had to install bluez-compat and then in a terminal run sudo hidd --search. With that the mouse was paired and works great!

The machine is surprisingly snappy. I did install a 2GB chip before I even turned the machines on though. After a full day of use I'm very happy with both the Asus 1000he and Ubuntu 9.04

Russ

Do you need to grab that special kernel if you're running Netbook Remix on 1000HE? Or is that kernel already implemented in Netbook Remix? Just asking, most of the hardware in 1000HE functioned in Netbook Remix.....I'm wondering if the kernel you suggest actually adds MORE functionality :)

---

### Post by RIT_girl on 2009-05-16
I have been running eeebuntu standard on my 1000 for the past 5 months...only one big issue with GRUB that has kept me from loving it. 

But you can buy extra RAM that really helps speed things up if you are worried about that, I got went to 2GB for 20 bucks. I didn't notice difference, but as been started the Atom isn't a big workhorse- this does internet, office, and I run a program or two through WINE, but nothing that takes a lot of thinking.

---

### Post by blueridgedog on 2009-05-16
> **enchantedsky said:**
> Do you need to grab that special kernel if you're running Netbook Remix on 1000HE? Or is that kernel already implemented in Netbook Remix? Just asking, most of the hardware in 1000HE functioned in Netbook Remix.....I'm wondering if the kernel you suggest actually adds MORE functionality :)

The new 9.04 netbook remix works on my 1000 without a special kernel.

---

### Post by rustutzman on 2009-05-16
I'm pretty sure NBR already has that kernel in  it.


Russ

---

