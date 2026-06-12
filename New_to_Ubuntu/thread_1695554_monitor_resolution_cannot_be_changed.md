---
title: "monitor resolution cannot be changed"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by vik.gelin on 2011-02-26
hello friends. 
i am having  the monitor resolution problem. recently i changed my motherboard from gigabyte to P4M800-M7 V:1.0 by ELITE GROUP. when i had gigabyte the resolution was good but now the resolution is just 640X400...

ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 640 x 350, current 640 x 400, maximum 640 x 400
default connected 640x400+0+0 0mm x 0mm
   640x400        85.0* 
   640x350        85.0  
ubuntu@ubuntu:~$ 

*-display UNCLAIMED
                description: VGA compatible controller
                product: KM400/KN400/P4M800 [S3 UniChrome]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f0000000-f3ffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)



i dont know what is the problem .
i have run my system from a live cd and from hard disc and from a live usb too...but everytime the resolution is same.currently i am running ubuntu 9.10 karmic from a live usb now.is it due to lack of hardware or due to some missing  drivers :confused:.i am not able to see full screensand problem in doing thngs as i cant see ful windows.i did tried to change it by selecting Display from Preference

---

### Post by Perfect Storm on 2011-02-26
This: KM400/KN400/P4M800 [S3 UniChrome]
Worst card (brand) you can use with Linux, as the S3 vendor hardly supports Linux.
But you could try with the latest version of Ubuntu and see if the S3 driver (newer), correct the error.

---

### Post by vik.gelin on 2011-02-26
> **Artificial Intelligence said:**
> This: KM400/KN400/P4M800 [S3 UniChrome]
Worst card (brand) you can use with Linux, as the S3 vendor hardly supports Linux.
But you could try with the latest version of Ubuntu and see if the S3 driver (newer), correct the error.
can u plz tell me how to renew the drivers.in this version?

---

### Post by Perfect Storm on 2011-02-26
> **vik.gelin said:**
> can u plz tell me how to renew the drivers.in this version?

You can't without recompiling it into the kernel (advanced, for experienced users).

You could try:
[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

---

### Post by brallan on 2011-02-26
that sounds like a lot of work. Any good reason you can't download (or torrent-download) one of the following and try it out?

[ubuntu 10.10]("http://www.ubuntu.com/desktop/get-ubuntu/download")
[ubuntu alpha daily build?]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by realzippy on 2011-02-26
..basically you need a xorg.conf file since the openchrome/VIA
driver does not support KMS (KernelModeSetting)...
If you install 9.10 or maybe 10.04 it should be possible
to get the driver running with your desired resolution.

---

### Post by vik.gelin on 2011-02-26
> **brallan said:**
> that sounds like a lot of work. Any good reason you can't download (or torrent-download) one of the following and try it out?

[ubuntu 10.10]("http://www.ubuntu.com/desktop/get-ubuntu/download")
[ubuntu alpha daily build?]("http://cdimage.ubuntu.com/daily-live/current/")
do u guys wanna me  download 10.10 and try if the problem is still there or not? i have run fedora 14 from a live cd.,fedora 14 installed in hard disc.and ubuntu 10.10  installed in a usb stick but still the resolution problem was there.help me what practical commands and thngs like tht i need to get it right.
thanks:guitar:

---

### Post by brallan on 2011-02-27
I googled the following:

KM400/KN400/P4M800 [S3 UniChrome] linux
KM400/KN400/P4M800 [S3 UniChrome] ubuntu
KM400/KN400/P4M800 [S3 UniChrome] xorg

and it seems lots of people have had this problem. I bet that if it&#347; solveable, you will find it by looking at these...

[http://ubuntuforums.org/showthread.php?t=1046278](http://ubuntuforums.org/showthread.php?t=1046278)
[http://ubuntuforums.org/showthread.php?t=1164426](http://ubuntuforums.org/showthread.php?t=1164426)
[http://ubuntuforums.org/showthread.php?t=1211580](http://ubuntuforums.org/showthread.php?t=1211580)
[http://ubuntuforums.org/showthread.php?t=1470204](http://ubuntuforums.org/showthread.php?t=1470204)

and

[http://www.taringa.net/posts/linux/2144375/Via-VT8235-S3-UniChrome-Integrated-Video-Km400_Kn400_P4m800.html](http://www.taringa.net/posts/linux/2144375/Via-VT8235-S3-UniChrome-Integrated-Video-Km400_Kn400_P4m800.html)

a quick look at these makes me believe it is possible to tweak your xorg.conf file to get it working, but if you want desktop effects, you may need to buy another card.

good luck!

---

