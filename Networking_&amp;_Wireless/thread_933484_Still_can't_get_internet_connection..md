---
title: "Still can't get internet connection."
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Ian dewhurst on 2008-09-29
Hi 

I am using the WPN111 device to connect to the internet but I still cannot connect.

I have the drivers installed correct information using network manager, wireless network devices shows the hardware is installed.

But the evil hardware is still not blinking have I missed something?

---

### Post by bobnutfield on 2008-09-29
Are you using ndiswrapper?

---

### Post by Ian dewhurst on 2008-09-29
Oh yeah latest version of ndiswrapper and using what appears as the correct driver for the netgear device (dragged it from my XP partition).

---

### Post by bobnutfield on 2008-09-29
OK, you may have already tried this, but, in case you haven't, type in a terminal:

> sudo ndiswrapper -l

See if it returns the dirver you have installed and the hardware is present.  Then:

> sudo modprobe ndiswrapper

There will be no output returned from this command, but see if the lights on the device turn on after running the modprobe command.  Don't forget you also need the .sys file for your driver.

---

### Post by itsjareds on 2008-09-29
I am using the same device and I had the same problems, but I finally figured it out. Are you using a WPA2 connection?

Also, you might want to upgrade to the v2.0 version of the WPN111 drivers if you're using v1.1. You can easily tell if you're using the 2.0 version if you have two .inf files in your NETGEAR/Drivers folder. If you see an athwpn and netwpn11.inf file in that folder, then you have v1.1.

Here are the files for the 2.0 driver: [netgear_v2.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=83057&d=1219873086")
Here are some packages you will need if you are using WPA2, or perhaps WPA and WEP: [ubuntu_packages.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=83059&d=1219873322") - Includes ndisgtk, ndiswrapper, and wicd. Don't install wicd unless you are using WPA2. Otherwise, just post here..

[Take a look at this tutorial I made]("http://ubuntuforums.org/showthread.php?t=901818")

---

### Post by Ian dewhurst on 2008-09-29
I get this when sudo ndiswrapper -l is entered into terminal
```

netwpn11 : driver installed
        device (1385:5F01) present

```

I have also tried sudo modprobe ndiswrapper nothing happens regarding the device.

Also I use a 64bit WEP key.

---

### Post by itsjareds on 2008-09-29
Try restarting your computer, and after it has successfully gotten restarted and is booting up, unplug and replug your wpn111. Then load into Ubuntu and tell me if that works. Sometimes this happens to me and it won't get a connection.

---

### Post by bobnutfield on 2008-09-29
I have looked at the link posted by **itsjareds** and it is a very thorough instruction.  This should get you going if you follow it.

---

### Post by itsjareds on 2008-09-29
I know that it took me a while to get the blue light blinking, but I can't remember what the problem was.. hopefully my tutorial will help :-s

---

### Post by Ian dewhurst on 2008-09-29
Hi thankyou for the tutorial, however it didn't work one thing that stood out for me was that you say it doesn't work under 64bit hardy, this where my problem may lie as I am running this.

Would it be recomended that I remove this and use the 32bit version? I have tried many times to reboot and plug in the device and it hasn't worked:(

---

### Post by bobnutfield on 2008-09-29
Is the Windows version that you got the driver from 32bit?  If so, you have discovered the problem.

---

### Post by Ian dewhurst on 2008-09-29
Yep this is where my problem lies I have asked my mums boyfriend and everything is 32 that was installed.

Right now I need to remove the ubuntu partition.

Thankyou all for your help (bobnutfield and itsjareds) for putting me into perspective. I shall report back tomorrow with my findings.

---

### Post by itsjareds on 2008-09-29
> **bobnutfield said:**
> Is the Windows version that you got the driver from 32bit?  If so, you have discovered the problem.

Yeah, I had installed x64bit Ubuntu also but NETGEAR *still* hasn't released a 64bit version for Vista and other users..](*,)

Just install 32bit if you can..

---

