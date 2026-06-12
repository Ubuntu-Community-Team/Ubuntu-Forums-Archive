---
title: "WG111v1 sometimes works other times is 'unknown'"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by willz06jw on 2007-03-03
Let me start by saying thanks for looking at my problem and helping me with it.

I am using Feisty 7.04 and I have been trying to set up a Netgear WG111v1 to connect to my wireless network in my house.  

I installed the right driver (the one that was proven to work on the ndiswrapper list)

It showed up, I connected to my network using WPA security, and it worked better than windows in managing my connection.  Then I restarted the computer :( When it started back up it could not see my adapter any more -- it showed up as Unknown Usb Device in HAL.

Here is what I got from my command line:
```

willz06jw@Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

willz06jw@Linux:~$ ndiswrapper -l
Installed drivers:
netwg111                driver installed, hardware present 

willz06jw@Linux:~$ ls /etc/ndiswrapper
netwg111

```

Any idea?

Thanks again,
William Howard

---

### Post by ingo on 2007-03-04
Though I am not familiar with ndiswrapper could it be that ndiswrapper is not started on boot? Cos if it did, it should bring the netwg111 driver to life...

Just my 2 cents' worth...

---

### Post by willz06jw on 2007-03-04
nope, it starts but it can't recognize it.

---

### Post by willz06jw on 2007-03-05
The problem was that when I connected the first time I installed a bunch of updates.  I think this updated my system to the new kernel and this causes a driver conflict with ndiswrapper.  And it didn't work from this point forward.

I fixed this problem by going to /etc/modprobe.d/blacklist and entering 
```
blacklist prism54usb
```
at the end of the file.

Restart and ndiswrapper will suddenly spring to life!

Will

PS:  If you don't want to restart you can also just take the drivers out that are being used right now by typin
```
sudo modprobe -r ndiswrapper
sudo modprobe -r prism54usb
sudo modprobe -i ndiswrapper
```

This will make it automatically work, but you still need to make sure that the driver is blacklisted , as described above, for it to work the next time you start your computer.

---

