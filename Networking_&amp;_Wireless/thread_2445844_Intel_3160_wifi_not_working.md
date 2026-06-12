---
title: "Intel 3160 wifi not working"
date: 2020-06-20
forum: Networking &amp; Wireless
---

### Post by glb1945 on 2020-06-20
The wifi on my intel i3 (3160) suddenly stopped working in 18.04 So I upgraded to 20.04 and it doesn’t work there either.
Were there changes in 18.04 that could have caused this? The command lshw -C network shows the adapter is there.
ANd  I loaded the u.code suggested by intel (14).  What else do I need to do? Thanks for your help.

Jerry

---

### Post by chili555 on 2020-06-20
Please run and post:

```
sudo modprobe iwlwifi
dmesg | grep iwl
rfkill list all
```Is this a dual boot with Windows?

---

### Post by glb1945 on 2020-06-20
[https://paste.ubuntu.com/p/r9jdM6GwH5/](https://paste.ubuntu.com/p/r9jdM6GwH5/)

modprobe no output
dmesg ouput in pastebin
rfkill bluetooth only

---

### Post by chili555 on 2020-06-20
Wow! That's one unhappy driver and hardware combination!

Please try:

```
sudo apt purge backports-iwlwifi-dkms

```
Reboot and show us:

```
sudo modprobe iwlwifi
dmesg | grep iwl
```

> WARNING: CPU: 2 PID: 434 at [COLOR="#FF0000"]/home/jerry/backport-iwlwifi/[/COLOR]drivers/net/wireless/intel/iwlwifi/pcie/trans.cDid you download and compile this yourself, Jerry?

---

### Post by glb1945 on 2020-06-20
Chioli,

I downloaded the ucode suggested by intel I placed it in /lib/firmware as told to do. Will do as you suggest and post the results.

---

### Post by glb1945 on 2020-06-21
[https://paste.ubuntu.com/p/fN3SxhkJmg/](https://paste.ubuntu.com/p/fN3SxhkJmg/)

backport not found

Here is output from dmesg after reboot

Jerry

---

### Post by chili555 on 2020-06-21
From your paste:

> Loading modules [COLOR="#FF0000"]backported from iwlwifi[/COLOR]If you did not install backport-iwlwifi-dkms, then you compiled and installed from source code or it came preinstalled when you bought the laptop. 

I previously asked:

> Did you download and compile this yourself, Jerry?How did backport get there???

---

### Post by glb1945 on 2020-06-21
Chili,

Because my computer is wireless, I had to move everything to another room to be able to use ethernet. I would guess that one site said to try some command that might have caused that, but I am not sure. 
Anyway that does not explain why 18.04 stopped working or why a fresh install of 20.04 did not work?

Jerry

---

### Post by glb1945 on 2020-06-21
chili,

is the driver for the Intel wifi  3160 adapter included in 20.04 or not?
if so then there should have been no problems. If not, then how to add the adapter.
of course the other possibility is a bug.

---

### Post by chili555 on 2020-06-21
> **glb1945 said:**
> chili,

is the driver for the Intel wifi  3160 adapter included in 20.04 or not?
if so then there should have been no problems. If not, then how to add the adapter.
of course the other possibility is a bug.
It and the required firmware are included by default. There is no need for any backported driver.

---

### Post by glb1945 on 2020-06-22
Chili,

i will I&#8217;ll do a fresh install of 20.04 and see if the 3160 works.

Jerry

---

### Post by chili555 on 2020-06-22
> **glb1945 said:**
> Chili,

i will I’ll do a fresh install of 20.04 and see if the 3160 works.

JerryI suggest that when the installer offers to install updates and proprietary drivers, etc., that you *NOT* accept. I wonder if this is how the backport driver got installed originally.

---

### Post by glb1945 on 2020-06-22
Chili,

I brought up 20.04 wirelessly from a usb stick. Wifi did not come up automatically so it seems to me that the driver is not included in 20.04?  If so wouldn’t the adapter been recognized and started?
Jerry

---

### Post by chili555 on 2020-06-22
From the USB live session, check to see if the wireless is turned off:

```
rfkill list all
```

Did the driver load?

```
lsmod | grep iwl
```

If not, load it:

```
sudo modprobe iwlwifi
```

And check for errors or other messages:

```
dmesg | grep iwl
```

May I assume the image you are trying to install is the normal desktop edition, not server or minimal or Kilngon??

> so it seems to me that the driver is not included in 20.04? It certainly is in the 20.04 install that I'm running right now to answer your post!

---

### Post by glb1945 on 2020-06-22
[https://paste.ubuntu.com/p/mQwRNttfKy/](https://paste.ubuntu.com/p/mQwRNttfKy/)

Chili,

No luck. Here is output from dmesg.

Jerry

---

### Post by glb1945 on 2020-06-22
Chili,

I thought I checked desktop. But I can double check. What is the easiest way to do that.

jerry

---

### Post by glb1945 on 2020-06-22
Chili,

uname -a states the generic version of the kernel is enabled

Jerry

---

### Post by chili555 on 2020-06-22
In your paste, we see:

> [    4.825962] iwlwifi 0000:02:00.0: Firmware not running - cannot dump error
[    6.784443] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110Searching for that exact error finds two interesting threads: [https://askubuntu.com/questions/1165176/intel-dual-band-wireless-ac-3165-not-detected-on-19-04](https://askubuntu.com/questions/1165176/intel-dual-band-wireless-ac-3165-not-detected-on-19-04)> 
So I tried 18.04 and it did not work. So I opened up the laptop to unplug the battery and while I was at it I wiggled the cables on the wifi card and now it seems to work on 18.04 and 19.04? I don't know why (**probably hardware related**) but I am not going to ask questions.

And also: [https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1727611.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1727611.html)> 
If it is failed without any changes like upgrading firmware version and 
motherboard bios then** we can suspect failure in the hardware**
As you have tried two installations and, without fail, get logs filled with errors, I also suspect a hardware failure.

As you can see, the driver iwlwifi loads on boot and the driver finds and loads firmware:

> [    2.641160] [COLOR="#FF0000"]iwlwifi[/COLOR] 0000:02:00.0: [COLOR="#FF0000"]loaded firmware version 17.3216344376.0 [/COLOR]op_mode iwlmvm
[    2.700385] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    2.719264] iwlwifi 0000:02:00.0: base HW address: 30:3a:64:49:2b:f9
[    4.744434] iwlwifi 0000:02:00.0: Failed to run INIT calibrations: -110
[    4.744441] iwlwifi 0000:02:00.0: Collecting data: trigger 16 fired.

The correct driver and firmware are clearly present in default Ubuntu 20.04.

---

### Post by glb1945 on 2020-06-22
Chili,

i will try an external adapter to see if that works. Thanks for all your help. I&#8217;ll 
let you know what happens.

Jerry

---

### Post by glb1945 on 2020-06-22
An external usb wifi adapter works. Thanks again for your help!

Jerry

---

