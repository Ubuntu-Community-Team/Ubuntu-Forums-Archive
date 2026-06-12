---
title: "This may be useful for ppl struggling with USB modems"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by rksk16it on 2008-05-27
Hi friends,

I am using a USB modem on my laptop, running Ubuntu 8.04. The modem is :
**Huawei Technologies Co., Lt. E620 USB Modem**

I would like to share my experience on how i got it working :
First, i downloaded the file [3g_USB_Modem.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=52426&d=1196934371")

There are 2 files in there excluding README :
1. mod.sh
2. wvdial.conf

In mod.sh i made some changes..the diff output is :
```
6,7c6,7
< modprobe usbserial vendor=0x12d1 product=0x1003
< mknod /dev/ttyUSBo c 188 0
---
> modprobe usbserial vendor=0x12d1 product=0x1001
> mknod /dev/ttyUSB0 c 188 0
10c10
< Wvdial 3g
---
> wvdial 3g internet
```

i looked up the exact product and vendor id of my modem by using the command :
```
lsusb -v
```

I also edited wvdial.conf, the edited version i post as attachment. As readme mentions we have to replace "internet" with the APN, i looked up the correct APN by first installing it in windows-XP :P. Also most of the changes i made i looked up info either from windows-XP's GUI based app they provided with modem and from this thread :
[http://ubuntuforums.org/showthread.php?t=329119]("http://ubuntuforums.org/showthread.php?t=329119")

After that i just followed there README and it worked fine. There is one thing to point out...
The readme says that we should execute /etc/mod.sh and then the command
(the command readme mentions is slightly different, i am stating the command i run
```
wvdial 3g internet
```
If we see mod.sh we can see that this command is already present in there, so it executed when we run mod.sh. But the problem is that this command doesnt work immediately after mod.sh is run, rather after 10 - 15 seconds.

So, in the end everything is working including firefox, synaptic manager, skype, evolution...except these problems :
1. This one is major : Pidgin is the only application i found which is not working. It says "waiting for network connection" :?:
2. This is minor (very minor) : Firefox and Evolution start in "offline" mode, though when mode is changed they work.
3. The network manager icon always show that no network is connected. :lolflag:

So, in the end if any1 got any ideas on that pidgin problem...or just any comments, i would be glad to hear :)

---

### Post by tigerplug on 2008-05-27
Thanks for this!

Have you got a link to a picture of this particular modem? Im using a similar one but not sure of the model number and I'm not at home. 

I haven't been able to connect to the internet with my USB 3G modem (on O2 Ireland) using Ubuntu because I don't know how to get it to work.


I'm dual booting Vista at the moment and the only reason that I haven't completely switched is the USB modem issue.

---

### Post by primky on 2008-05-27
Thanks, i will try this. I have Siemens SGH Z150 as modem though. Will report how it went.

*/ EDIT: Do you have to install drivers for modem first? If yes, this has no point for me, as i can't find Linux drivers for my modem :(

---

### Post by rksk16it on 2008-05-27
> **tigerplug said:**
> Thanks for this!

Have you got a link to a picture of this particular modem? Im using a similar one but not sure of the model number and I'm not at home. 

I haven't been able to connect to the internet with my USB 3G modem (on O2 Ireland) using Ubuntu because I don't know how to get it to work.


I'm dual booting Vista at the moment and the only reason that I haven't completely switched is the USB modem issue.

Remove the modem and run "lsusb" and then insert it again and run "lsusb" again. Hopefully the difference will show u the model of ur modem :)

> **primky said:**
> Thanks, i will try this. I have Siemens SGH Z150 as modem though. Will report how it went.

*/ EDIT: Do you have to install drivers for modem first? If yes, this has no point for me, as i can't find Linux drivers for my modem :(

No, i havent installed any additional linux drivers.

---

### Post by tigerplug on 2008-05-27
> **rksk16it said:**
> Remove the modem and run "lsusb" and then insert it again and run "lsusb" again. Hopefully the difference will show u the model of ur modem :)



No, i havent installed any additional linux drivers.



Thanks, I'll try that at the weekend when I get a chance!

---

### Post by Nikitas350 on 2008-05-28
see [http://ubuntuforums.org/showthread.php?t=800179&highlight=offline+networkmanager](http://ubuntuforums.org/showthread.php?t=800179&highlight=offline+networkmanager) it's a problem of network manager i think.

---

### Post by rksk16it on 2008-05-28
> **Nikitas350 said:**
> see [http://ubuntuforums.org/showthread.php?t=800179&highlight=offline+networkmanager](http://ubuntuforums.org/showthread.php?t=800179&highlight=offline+networkmanager) it's a problem of network manager i think.

Thanks for the point. I already figured it out that it is a Network Manager's problem, so i just set my eth0 to DHCP in there and every app is happy now. :)
Changing that configuration option which u mentioned in that forum is a better idea though. :)

---

### Post by knetcozd on 2008-11-26
for those of you who want an easier method of starting  wvdial dialer, you can also create an "executable" ,which you can click to start the internet , just find your wvdial dialer "executable" by typing where is wvdial into konsole/terminal, copy the dialer and paste on your desktop,simple as that ,now you don't have to type wvdial [dialer] everytime you want to start the internet.

---

