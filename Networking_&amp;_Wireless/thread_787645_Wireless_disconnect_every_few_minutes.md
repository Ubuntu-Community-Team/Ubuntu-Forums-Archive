---
title: "Wireless disconnect every few minutes"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by tzach on 2008-05-09
First, let me admit I'm an absolute beginner in Ubuntu.
I have a brand new desktop dual Intel cpu system, with EDIMAX PCI wireless card, and a 8.04 desktop (kernel 2.6.24-16-rt)

Initially the system recognized the WiFi and connoted, but the connection is lost after a few minute of use, and a restart is required.
The WiFi is open and does not require password (only MAC filtering).

Any help would be appreciated.

Thanks
Tzach

---

### Post by brazh on 2008-05-09
I had similar problem. I think, it was because of network-manager. I've removed it and installed Wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)). After that everything works smoothly. The only difference is that I'm using WPA-security settings with MAC-filtering, but I think it doesn't matter.

---

### Post by tzach on 2008-05-09
Thanks, I will try it.
How do I remove the network-manager? (I am a newbe)

---

### Post by tzach on 2008-05-09
OK, the Wicd automatcly uninstall the standard network-manager.
Now I have it install and running, hopfully with out problems.
Thanks for the help brazh.

---

### Post by tzach on 2008-05-14
After a few more days of testing - the problem was not solved.
The warless connection is disconnecting after a few minutes of works.
I notice it happen relatively fast when I'm opening multiple tabs on Firefox, but I'm not sure there is a correlation.

At this point, any idea will be more than welcome.

Thanks
Tzach

---

### Post by alex1973 on 2008-05-15
This is happening to me as well since I've upgraded to Hardy. I've never had this problem with the previous 3 Ubuntu releases. I must mention that it works without problems from Windows.

---

### Post by Flame0001 on 2008-05-25
I'm also having the same problem with Wicd using the broadcom driver.

---

### Post by dm6257 on 2008-05-25
This is the same problem I started having since the new kernel was installed last night.  I am using a Thinkpad Z61 with the Intel PRO/wireless interface that works fine with Vista on the same machine.  dm6257

---

### Post by muzehyun on 2009-04-18
I have exactly same problem.
I don't have solution yet but I have a workaround for the problem.

[http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html](http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html)

It's working for me.

---

### Post by jengurule on 2010-10-17
I need to know if this will work, and if so...how do I go about doing this...I am a newbie, and being continuously disconnected is driving me insane!!

---

### Post by pawnrocket on 2010-11-28
###Update, this has not resolved the issue. sorry.

I am also experiencing the same it issue on Maverick. The ath9x driver could be the issue. I have tried the latest main line kernel and it seems to have resolved the issue. 

The mainline can be found here

[https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

However you could run into more issues using it. 

I also made an attempt to build the latest kernel from kernel.org. For some reason that didn't resolve the issue. 

You can also try the backports method which might be a little better then using the mainline kernel

That can be found here

[http://ubuntuforums.org/showthread.php?t=1205318]("http://ubuntuforums.org/showthread.php?t=1205318")

I hope this is helpful.

---

### Post by Bladerunner0324 on 2013-01-27
I had a very similar problem when I upgraded to Ubuntu 12.04. I could connect to the wireless network but it would only stay connected for a few seconds. Try going into 'Edit Connections...' by right clicking your network icon and under Wireless edit the connection you're having trouble with and in 'Wireless Security' make sure the Key or Password is there and click save. This worked for me and I haven't had trouble since.

---

### Post by howefield on 2013-01-27
Old thread closed.

Please feel free to start a fresh one.

---

