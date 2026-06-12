---
title: "Installing Wireless Adaptor"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by LaLibertine on 2009-09-23
So, I downloaded Ubuntu today for the first time ever (9.04.) I've never used it before in my life. I really like it so far. I was told that a lot of things might require a little more work, and I'm fine with that. Learning is good.

But I'm trying to install my wireless USB adapter, and I'm stumped. It's a Netgear RangeMax Wireless-N. The box says the model is WN111, but the disc and the USB itself says WN111v2, if that makes any difference. 

I've been trying to follow the instructions at [http://ubuntuforums.org/showthread.php?t=859481](http://ubuntuforums.org/showthread.php?t=859481) (mainly following Skulled's instructions) but I'm not making any progress. Frankly, I don't even know if I'm reading it right. 

Also, I've downloaded two versions of ndiswrapper: ndiswraper-utils-1.9 (which I get the message "Error: Wrong architecture 'amd64'") and ndiswraper-common.

Basically, I have no idea what I'm doing or looking at. Help. Please.

---

### Post by lkraemer on 2009-09-24
The link you furnished has very good detailed information.
Maybe you need to read a bit more about ndiswrapper, then
read Skulled's posting again.
[https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

Open a Terminal window, Copy and paste these commands (one at a
time), then post the output of the following commands:
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist 
               OR for >= 9.04 use cat /etc/modprobe.d/blacklist.conf

iwconfig

```
Then post the output.

Once you know what is already installed, and what the device is, you
might have to blacklist some drivers, then use ndiswrapper to install
the Windows drivers. You should be able to make it work.

Ref:
[https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

Good Example - once you get the *.inf file:
[http://ubuntuforums.org/showthread.php?t=859481](http://ubuntuforums.org/showthread.php?t=859481)
Posting #8

lk

---

### Post by ibuclaw on 2009-09-24
The posting of:
```
lsusb
```
Would prove most useful.

As if your device **really is** the W111v2, then you should have the V/P ids of: **0846:9001**.
If so, then I can tell you that this card is supported in the 2.6.31 kernel (that the next version of Ubuntu will be releasing with in 1 months time).

Regards
Iain

---

### Post by 3rdalbum on 2009-09-24
> **LaLibertine said:**
> Also, I've downloaded two versions of ndiswrapper: ndiswraper-utils-1.9 (which I get the message "Error: Wrong architecture 'amd64'") and ndiswraper-common.

You need both packages. I believe they should be on the Ubuntu CD? It seems like you're running 32-bit Ubuntu, so make sure you download the "i386" version.

---

