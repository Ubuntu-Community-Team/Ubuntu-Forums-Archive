---
title: "Netgear WG111v1 - Feisty - ndis says its there"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by willz06jw on 2007-03-01
Howdy,

I just installed Feisty to try to make the wireless easier -- still having a problem and a half :(.

My Netgear WG111v1 doesn't show up in the Network panel.  By this I mean there is no Wireless control listed - just Wired and Modem.  I installed the Windows driver using ndiswrapper and "ndiswrapper -l" says the hardware is present and the driver working.

Why doesn't Wireless show up on the network control?

Thanks for all of your help!
Will

---

### Post by Kobalt on 2007-03-01
Hello,

Can you post the output of the following command lines please : 
```
ls /etc/ndiswrapper
```
```
iwconfig
```

---

### Post by willz06jw on 2007-03-01
willz06jw@Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

willz06jw@Linux:~$ ndiswrapper -l
Installed drivers:
netwg111                driver installed, hardware present 

willz06jw@Linux:~$ ls /etc/ndiswrapper
netwg111


Thanks again,
Will

---

### Post by willz06jw on 2007-03-02
Fixed the problem:

Sor for any other Netgear WG111v1 users here it is:

The problem was I was using the WG111_SW1.2Beta13 zip file and not the correct "Initial driver release" from [http://kbserver.netgear.com/products/wg111v1.asp](http://kbserver.netgear.com/products/wg111v1.asp)

This file downloads as a .exe file so you gotta install two files to get the .inf file out of it:
(Note I figured out this by reading a post by someone on the ndiswrapper list)

(Note: You download these two programs just using the synaptec package manager in the System/Administration menu)

D/L and use the cabextract program on the exe you downloaded from netgear.
I think the command line usage is "cabextract wg111_setup.exe"

Then D/L and use the unshield program on data1.cab file
I think the command line usage is "unshield x data1.cab"

Once you did that you will have extracted a bunch of directories to where ever you ran the command.

go into the PreIntallXp directory  (cd PreIntallXp) and then move netwg111.inf and wg111nd5.sys into whatever directory you are going to load from every time.

Now that you have the files just do the normal ndiswrapper setup on them -- ndiswrapper -i netwg111.inf --- this will load it up and should work perfectly from now on.

Thank to the rest of the Ubuntu community for the help

Will

---

### Post by willz06jw on 2007-03-03
I am having another problem where it works sometimes and other times it doesn't.  It sometimes shows up as an unknown device.   So...I am starting a new post about it -- you can search on WG111 or WG111v1 to find it.


Will

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

### Post by willz06jw on 2007-03-11
[sigh] another update...

I can now get my WG111v1 to connect to the internet everytime.  The problem is that to do it I have to remove and reinstall the ndiswrapper driver every time I reboot.

I do this by the following code for anyone interested:
```
sudo modprobe -r ndiswrapper
sudo modprobe -i ndiswrapper
```

I have the ndiswrapper configuration file in modprobe, hence the remove command, but it doesn't load my driver before boot.  Does anyone know why?

Will

---

