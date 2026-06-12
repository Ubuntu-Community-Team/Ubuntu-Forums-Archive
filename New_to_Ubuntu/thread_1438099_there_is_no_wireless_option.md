---
title: "there is no wireless option"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by ni ni on 2010-03-24
hello all,

i usually turn on the laptop and i must enter the default keyring password (i think.  i haven't used this since january).  i'm not doing that now.

Now in the task bar there is no mention of wireless, it just has the wired network.  so it's not that i can't connect to my preferred wireless network but there is absolutely no mention of the wireless.


Please help x x x x:KS:KS

---

### Post by readycarpenter on 2010-03-24
> **ni ni said:**
> hello all,

i usually turn on the laptop and i must enter the default keyring password (i think.  i haven't used this since january).  i'm not doing that now.

Now in the task bar there is no mention of wireless, it just has the wired network.  so it's not that i can't connect to my preferred wireless network but there is absolutely no mention of the wireless.


Please help x x x x:KS:KS

some laptops now have a switch in the front or side to turn on/off the wireless card, this is the same as physically removing the hardware, it sounds to me like ubuntu does not see you have a wireless card connected

also have you updated your system lately, what possibly triggered your problem?

---

### Post by wojox on 2010-03-24
Sounds like the driver crashed. Check Hardware Drivers and see if theirs anything to activate. Or you may need to reinstall. What does this produce:

```
lspci | grep -i net
```

---

### Post by ni ni on 2010-03-24
i get:
```
niamh@niamh-laptop:~$ lspci | grep -i net
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
niamh@niamh-laptop:~$
```

I went into Hardware Drivers and hallelujah! it said  i had to install a driver.  so i did, and even after a restart it hasn't solved the problem :-/

the problem must be the modem's driver, but also why doesn't it ask me to unlock the default keyring anymore???

Thanks for your help readycarpenter and wojox x x x

---

### Post by ni ni on 2010-03-25
this is what i know about my laptop:
Intel Celeron M processor 1.60GHz
1.59GHz, 448 MB RAM
VIA/S3G UniChrome Pro IGP
X86-based

it's very old, and it over heats like mad.

ubuntu has suddenly decided it needs a propriety driver!

[PHP]The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa supportand intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.

This driver is activated and currently in use.[/PHP]

---

