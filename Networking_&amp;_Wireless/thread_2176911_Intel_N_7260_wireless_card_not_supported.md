---
title: "Intel N 7260 wireless card not supported"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by Anna_Baas on 2013-09-26
Hi all,

My partner just installed Ubuntu 13.04 on his custom notebook. Apparently it's a bit *too* custom, as almost all Intel wireless cards seem to be supported OOTB, but not the N6235.

I read something about backporting, but it's all Greek to me. I also found what's supposedly the driver ([iwlwifi-6000g2b-ucode-18.168.6.1.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000g2b-ucode-18.168.6.1.tgz"), via [this page]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm")) but can't get that one installed either!

Any tips before I get frustrated to the point of cracking the thing open and installing a different card?

---

### Post by Bucky Ball on 2013-09-26
*Thread moved to **Networking & Wireless**.*

Welcome. You might have more luck here. 

My suggestion: Plug in an ethernet cable and update then reboot. 

Run these two commands in a terminal (don't worry, nothing tricky), one after the other, pressing return between. Just copy and paste one at a time if you like:

```
sudo apt-get update
sudo apt-get upgrade
```

Restart the laptop with the cable out. What does the network icon look like? Does it show available network when you left click it?

This has been known to fix it in 13.04. Good idea to update a new install first up. ;)

---

### Post by Anna_Baas on 2013-09-26
Thank you for the suggestion and the move!

I did update (fortunately that works just like Debian :) ). Now ethernet stopped working as well, although it did before. Not quite as expected.

The icon looks like an empty quarter circle.

---

### Post by varunendra on 2013-09-26
Please open the terminal (ctrl-alt-T) and post back the outputs of the following commands -
```
uname -mr
lspci -nnk | grep -iA2 net
dmesg | grep iwl
```

---

### Post by Anna_Baas on 2013-09-27
```
uname -mr
```
3.8.0-30-generic x86_64

```
lspci -nnk | grep -iA2 net
```
02:00.0 Network controller 0280: Intel Corporation Device 8086:08b1 (rev 63)
Subsystem: Intel Corporation Device 8086:4070
03:00.0 Unassigned class ff00: Realtek Semiconductor Co., Ltd. Device 10ec:5289 (rev 01)

03:00.2 Ethernet controller 0200: Realtek Semiconductor Co., Ltd RTL8111/8168 
PCI Express Gigabit Ethernet controller 10ec:8168 (rev 0a)
Subsystem: CLEVO/KAPOK Computer Device 1558:0540

```
dmesg | grep iwl
```
2.084387 iwlwifi 0000:02:00.0 irq 43 for MSI-MSI-X
2.509834 iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-7260-6.ucode' falied.
2.509842 iwlwifi 0000:02:00.0: no suitable firmware found!

(There's a lot more square brackets in there, but I was afraid the forum would eat them...)

---

### Post by chili555 on 2013-09-27
I hope Varun will accept a little hint. First, you haven't got a 6235; you have a 7260:> request for firmware file 'iwlwifi-[COLOR="#FF0000"]7260[/COLOR]-6.ucode' falied.Here is the method to compile the 7260 driver and install its firmware: [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63)

---

### Post by varunendra on 2013-09-28
Haha... I was about to point to that solution of yours just by reading "Intel N **6235**" in the title, only wanted to make sure first. :P

---

### Post by Anna_Baas on 2013-09-28
IET WORKS

Thank you so much!

Question remains why the store gave us a *better* (or, at least, better-specced and more expensive) card than ordered without telling us. But that's probably not something for the forum ;)

---

### Post by varunendra on 2013-09-28
> **Anna_Baas said:**
> Question remains why the store gave us a *better* (or, at least, better-specced and more expensive) card than ordered without telling us.

Demand Vs Production/Availability issues maybe?

By the way -
> **Anna_Baas said:**
> (There's a lot more square brackets in there, but I was afraid the forum would eat them...)
It wouldn't eat anything, nor would change codes to smileys if you put the outputs too in the code box (like you did with the commands) :P

And thanks for the confirmation, this card is very new, and "It works" confirmations are like energy boosters for us ! :D

---

### Post by Anna_Baas on 2013-09-28
> **varunendra said:**
> Demand Vs Production/Availability issues maybe?

Probably. They first told us it'd be delayed because they were waiting for a component, then a minute later we received a shipping notice. Good chance they decided to just plug in what they had available.

Still, it would have been nice if they'd mentioned it, would have made the googling a lot more productive :) (but it taught me to never trust the spec sheet and just check for myself, so that's a positive.)

> **varunendra said:**
> 
By the way -

It wouldn't eat anything, nor would change codes to smileys if you put the outputs too in the code box (like you did with the commands) :P

Good to know :) I must say, I had so much fun helping my dad install ubuntu on his desktop and now my partner on his notebook, I might go back to dual-boot on my trusty macbook. In which case I'll probably come here more often and your tip will come in handy ;)

> **varunendra said:**
> 
And thanks for the confirmation, this card is very new, and "It works" confirmations are like energy boosters for us ! :D

We're very grateful! If you have a cause you'd like to receive a flattr or a small donation, just say the word :) 

And I was wondering about the very new thing actually - why does it need a backport if it's so new? Does Intel use old firmware?

---

### Post by varunendra on 2013-09-28
> **Anna_Baas said:**
> If you have a cause you'd like to receive a flattr or a small donation, just say the word :) 
Probably the developers who create and develop these small pieces for open source community deserve it the most. We are just making use of the hard work 'They' have done, and getting credits most of which should actually go to them.

> And I was wondering about the very new thing actually - why does it need a backport if it's so new? Does Intel use old firmware?

Lol!! Just rotate your perspective about 180 degrees - consider it from the perspective of "Driver --> to --> System", not "System --> to --> Driver".

Newer Driver ---> back-ported to ---> Older system

So "Backported driver" means a "Newer Driver" which is "ported backwards (made compatible)" to a relatively "Older OS (kernel)".

The driver you are currently using was actually developed for kernel 3.11 (hence the package name), which is newer than the kernel you are currently using. The concept of backported drivers was implemented so that users can get the benefit of newer drivers without having to upgrade the whole kernel/system.

---

### Post by Anna_Baas on 2013-09-28
> **varunendra said:**
> 
Lol!! Just rotate your perspective about 180 degrees - consider it from the perspective of "Driver --> to --> System", not "System --> to --> Driver".

Newer Driver ---> back-ported to ---> Older system

So "Backported driver" means a "Newer Driver" which is "ported backwards (made compatible)" to a relatively "Older OS (kernel)".

Ha! Got it. Duly rotated. Thank you. (I think I got confused because of a thread where they used a backporting package from an older version of the distro.)

---

### Post by chili555 on 2013-09-28
Glad it's working! When update manager installs a new kernel version, known as linux-image, you will need to compile the driver for your newer kernel.```
cd Desktop/backports-3.11-rc3-1/
make clean
make defconfig-iwlwifi
make
sudo make install
```Please retain the files and these instructions for that day. You needn't reinstall the firmware.

The driver doesn't exist in your 3.8.0-30 kernel because the device uses 802.11AC technology which wasn't actually in existence when kernel 3.8 was released in February of 2013. [http://en.wikipedia.org/wiki/802.11ac](http://en.wikipedia.org/wiki/802.11ac)> ...with final 802.11 Working Group approval and publication scheduled for early 2014.

---

### Post by Anna_Baas on 2013-09-28
You've seriously got me very impressed with the forum community. I came here tail between legs to ask why THE THING WASN'T WORKING. AGAIN. WHY. and the answer was already waiting :)

---

