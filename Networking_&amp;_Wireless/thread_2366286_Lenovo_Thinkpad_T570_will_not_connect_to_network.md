---
title: "Lenovo Thinkpad T570 will not connect to network"
date: 2017-07-15
forum: Networking &amp; Wireless
---

### Post by Vikram_Kumaran on 2017-07-15
I recently jumped the gun on Installing Ubuntu on my new Thinkpad, but for some reason, it will not connect to my network at all via wireless or ethernet. Considering I had the same problem with my last laptop, I followed the guidelines of the forum and attached the diagnostic file as requested. Seriously, the whole reason I got this laptop was that it was supposedly Linux friendly.

---

### Post by vocx on 2017-07-15
> **Vikram_Kumaran said:**
> I recently jumped the gun on Installing Ubuntu on my new Thinkpad, but for some reason, it will not connect to my network at all via wireless or ethernet. Considering I had the same problem with my last laptop, I followed the guidelines of the forum and attached the diagnostic file as requested. Seriously, the whole reason I got this laptop was that it was supposedly Linux friendly.
Who told you this laptop was Linux friendly?

If this is a recent model, like released this year 2017, it may be possible that you need a more recent kernel to handle the specific hardware that it has.

It seems you are running 16.04 with a 4.4.0-31 kernel, which is a slightly old kernel. I bought 2 years ago the Thinkpad T450s, and I installed 16.04 as it became available. I guess at that time it installed the same kernel you currently have. As I recall my hardware was supported out of the box without problems. A year and a half later, after normal updates, the kernel is in version 4.4.0-83, and everything keeps working fine.
```

# mine
##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-V [8086:15a3] (rev 03)
    Subsystem: Lenovo Ethernet Connection (3) I218-V [17aa:2227]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5210]
    Kernel driver in use: iwlwifi

```

I would suggest you try a newer Ubuntu, 16.10 or 17.04, so that you get to try a newer kernel, either 4.8.x, or 4.10.x. If it works, I suggest you keep that version of Ubuntu. If you really want to have a long term support version (LTS), I suggest you install 16.10 or 17.04, and upgrade successively to 18.04 when it is released in 2018, and then stay in that version.

Another possibility. If say, 17.04 works, make note of which kernel it is using. Then try to install that kernel version back into 16.04. Exactly how to do this, I'm not sure. Maybe you need to get the appropriate kernel package "linux-image-4.8.generic" as a debian package ".deb", and move it to your current 16.04 and install it.

---

### Post by chili555 on 2017-07-15
Please run these terminal commands and post the result:```
sudo modprobe iwlwifi
modinfo iwlwifi | grep 24FD
sudo modprobe e1000e
```Thanks.

---

### Post by QIII on 2017-07-15
Before we start suggesting re-installs, particularly of interim releases that will force subsequent reinstalls, let's have folks help with some general diagnosis first.  There msy be no need at all for reinstallation.

---

### Post by Vikram_Kumaran on 2017-07-15
I got nothing back whrn i ran them in the terminal. Did I do it wrong?

---

### Post by vocx on 2017-07-15
> **Vikram_Kumaran said:**
> I got nothing back whrn i ran them in the terminal. Did I do it wrong?
You should not get output after running the "modprobe" commands. They basically just load the modules "iwlwifi" and "e1000e". If there is no error, it will give no output.

See my post #2. These modules are the ones in use in my system, so presumably they should be used in your system as well. The module "iwlwifi" is for wireless and "e1000e" is for Ethernet.
```

sudo modprobe iwlwifi
sudo modprobe e1000e

```

The other command searches for information on the "iwlwifi" module.
```

modinfo iwlwifi | grep 24FD

```

If you get no output, it means the string "24FD" is not found in the output of the command "modinfo iwlwifi". In my system it also gives no output.

It does not mean you did it wrong, but possibly that your hardware is unsupported. Could you download Ubuntu 16.10 or 17.04, make a bootable USB, and try the live session that way?

---

### Post by Vikram_Kumaran on 2017-07-15
Give me some time to create a bootable 17.04 and run it. Will report with results soon.

---

### Post by chili555 on 2017-07-15
> It does not mean you did it wrong, but **possibly that your hardware is unsupported**. Could you download Ubuntu 16.10 or 17.04, make a bootable USB, and try the live session that way?It means -- exactly -- that your wireless is not supported. When you run 17.04, your wireless should work perfectly.

---

### Post by Vikram_Kumaran on 2017-07-15
Currently typing this from 17.04, Thank you guys so much.

---

### Post by vocx on 2017-07-15
> **Vikram_Kumaran said:**
> Currently typing this from 17.04, Thank you guys so much.
Maybe you can run the wireless script once more, just to see the modules, and for future reference.

Remember that you now have 17.04. In a few months 17.10 will come out, and the next long term support (LTS) version is 18.04. If you want the LTS version you have to upgrade twice, once to 17.10 and then to 18.04. Then you may wish to stay there.

---

