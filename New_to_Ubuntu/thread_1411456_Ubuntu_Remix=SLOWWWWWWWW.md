---
title: "Ubuntu Remix=SLOWWWWWWWW"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by myolbug on 2010-02-20
I just partitioned the drive on my Gateway NV52 laptop and installed Ubuntu Remix for netbooks on it.  It has Win7 on it now, but DAMN, something went wrong! 
It is 1970's slow, like ridiculous!  I finally just rebooted it and went back to Windows.

The specs on my laptop are:
AMD Athlon™ 64 X2 dual-core processor QL-62/QL-64/QL-65 (1 MB L2 cache, 2.02.1/2.1GHz, DDR2 667 MHz, 35 W)
Chipset 	AMD M780G/SB700 Chipset
Memory1, 4, 5, 	Up to 2 GB of DDR2 667 MHz memory, upgradeable to 4 GB using two soDIMM modules6  I have 4 gigs.	

ATI Radeon™ HD 3200 Graphics9 with up to 19198 MB of HyperMemory™ (256 MB of dedicated system memory, up to 1663 MB of shared system memory), supporting Unified Video Decoder (UVD), OpenEXR High Dynamic-Range (HDR) technology, Shader Model 4.0, Microsoft® DirectX® 10.0 

I know that ATI isn't the best for Linux, but there has got to be something else.

Any ideas?  This machine is only two or three weeks old and it is still practically empty.

---

### Post by 416inversed on 2010-02-20
I could be wrong, but I believe UNR is only made for Intel 32 bit processors, while your specs state an AMD 64bit. 

Try installing Ubuntu desktop for AMD 64 bit processors.

EDIT: I doubled checked and I was correct.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Has the correct ubuntu-9.10-desktop-amd64.iso
[URL="http://releases.ubuntu.com/karmic/ubuntu-9.10-desktop-amd64.iso"]
[/URL]

---

### Post by jimrz on 2010-02-20
> **myolbug said:**
> I just partitioned the drive on my Gateway NV52 laptop and installed Ubuntu Remix for netbooks on it.  It has Win7 on it now, but DAMN, something went wrong! 
It is 1970's slow, like ridiculous!  I finally just rebooted it and went back to Windows.

The specs on my laptop are:
AMD Athlon&#8482; 64 X2 dual-core processor QL-62/QL-64/QL-65 (1 MB L2 cache, 2.02.1/2.1GHz, DDR2 667 MHz, 35 W)
Chipset 	AMD M780G/SB700 Chipset
Memory1, 4, 5, 	Up to 2 GB of DDR2 667 MHz memory, upgradeable to 4 GB using two soDIMM modules6  I have 4 gigs.	

ATI Radeon&#8482; HD 3200 Graphics9 with up to 19198 MB of HyperMemory&#8482; (256 MB of dedicated system memory, up to 1663 MB of shared system memory), supporting Unified Video Decoder (UVD), OpenEXR High Dynamic-Range (HDR) technology, Shader Model 4.0, Microsoft® DirectX® 10.0 

I know that ATI isn't the best for Linux, but there has got to be something else.

Any ideas?  This machine is only two or three weeks old and it is still practically empty.

the "remix" is intended for **netbooks** with Atom processors NOT your dual core athlon **notebook**. try using the standard ubuntu or kubuntu or whichever (use either 32 or 64 bit version, your choice) and you should see considerable improvement. picking the proper version will make a huge difference. I run the remix on my Dell mini and standard ubuntu desktop on my Thinkpad with core2duo T9300 and both are anything but slow.

---

### Post by NightwishFan on 2010-02-20
You might not have direct rendering supported. The Netbook Launcher performs badly when using software rendering.

Here is some help with ATI:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?p=7996934#post7996934](http://ubuntuforums.org/showthread.php?p=7996934#post7996934)

---

### Post by myolbug on 2010-02-20
Well, I spoke too soon.  It installed 222 updates and then I set up the ATI drivers and now it is running a LOT faster.  However, will download the correct version and install it tomorrow.  But, it is moving quite well now.

---

### Post by 3rdalbum on 2010-02-20
It was the ATI drivers that caused the speed to improve. Without 3D acceleration, the netbook launcher interface will be very slow indeed.

Netbooks (as opposed to your machine, a notebook) mostly use Intel graphics processors which are supported with 3D out-of-the-box on Linux.

---

### Post by myolbug on 2010-02-20
Well, it is working well, I definitely like regular Ubuntu better.  Remix is just set up kind of inconveniently.  It is however FAST!  It uses both cores etc and no issues, just the setup is weird.

I am looking forward to seeing how regular Ubuntu will work.  Do you know if it will be faster, slower or the same?  Also, when I install it, is there anything I should know as far as the partitioning goes?  Will it give me the ability to install over the Remix partition?  Anything I should be aware of, quirks or whatnot?

Also, do you think this computer can handle Compiz or should I just leave that out?  It's fun to have all the goodies, but not necessary.

Thanks!

---

### Post by NightwishFan on 2010-02-20
My machine uses an integrated gpu and I run compiz fine. If you even have any dedicated video memory it should run well, if not it should still work.

---

### Post by myolbug on 2010-03-08
> **NightwishFan said:**
> My machine uses an integrated gpu and I run compiz fine. If you even have any dedicated video memory it should run well, if not it should still work.

Hey NightwishFan, I tried using the Normal or extra setting on my notebook, I guess that the combo of the GPU/processor on my machine can't quite do it.  No biggie really, I have all kinds of things turned on on my desktop at home.

There is a definite speed difference between Win7 and Remix.  Just on the net alone pages load in about half the time as Win7.  Startup is faster, programs load faster...  It seems like a different machine depending on which OS I use.

---

