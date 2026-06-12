---
title: "Wi-Fi causing lag on other devices at home"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by mithen2 on 2013-10-27
When I'm using Wi-Fi at home on my Laptop with Ubuntu 12.04 32bit it causes major delay on other devices at home such as iPad, Mac Book Air, iPhones.

 My Laptop is a HP Probook 6465b. I did "sudo lshw -short" in Terminal to get hardware details for my Wi-Fi card:

BCM4313 802.11bgn Wireless Network Adapter

When I disable Wi-Fi on my laptop and plug in an Ethernet cable the lag/delay on other devices is fixed and they all go back to running normally. What is the problem here?

---

### Post by varunendra on 2013-10-27
> **mithen2 said:**
> BCM4313 802.11bgn Wireless Network Adapter

The problem you mentioned is a common symptom of a problem with the proprietary driver "wl" that this card uses. Fortunately, there is a native driver which usually works better than the proprietary one in newer kernels.

Please check which kernel you are using -
```
uname -r
```
If it is 3.8 or later, please try -
```
sudo apt-get purge bcmwl-kernel-source
```
..then reboot. You should have a working wireless, hopefully better this time.

You may try above even if you have an older kernel, but the native driver wasn't as good on them.

If this doesn't solve your problem please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mithen2 on 2013-10-27
Hi I've done what you said. My kernal was 3.8 and I did the Terminal command you said and rebooted. How can I test if the Wi-Fi is working better than before? Normally my Dad has to shout at me because the Wi-Fi on his devices are lagging. 

Could you also explain to me what that Terminal command did?

```
sudo apt-get purge bcmwl-kernel-source
```

Super User do (that's me) purge (delete or remove) I'm guessing bcmwl is a wireless driver? So that's the proprietary driver from the manufacturers or HP? Where would the native drivers come from to replace them? Or are they preinstalled into the Ubuntu repository?

---

### Post by varunendra on 2013-10-27
> **mithen2 said:**
> How can I test if the Wi-Fi is working better than before? Normally my Dad has to shout at me because the Wi-Fi on his devices are lagging.
One of the most convincing test would be to start using the net as intensively as you can (that doesn't mean torrents, they can hog any network anytime) as soon as your Dad starts using his wifi devices. If you don't get shouted at again, bingo ! :P

Ok, seriously, if you don't notice a degradation, then it is an indication of improvement in itself. Because the proprietary driver doesn't support N channel, while the native one does. If it doesn't experience a problem with N-channel mode, then it means it is ready to give you a superior performance where possible. As for whether it is or can be 'hogging' the network like before, the only way to test is something similar as I advised above. ;)

> Could you also explain to me what that Terminal command did?
Sure, although you have already understood it correctly, I'll just confirm.

"sudo" (do as SU) is for running a command as Super User.
"apt-get" is the package manager.
Purge is same as "remove", but it also removes (or resets) all the configuration files created or modified by the package you are purging.
The "bcmwl-kernel-source" is the driver package that builds the driver "wl" during installation.

So, "sudo apt-get purge bcmwl-kernel-source" removes the "wl" driver, uninstalls its source package and removes all its settings and configuration files restoring the defaults.

One of the custom settings it made was to "Blacklist" the native driver "brcmsmac" which also supports this card. It does so to avoid conflict over resources. Purging "wl" driver removes it from blacklist so that it can load again during startup. This driver is a part of the kernel (like many others) and is ready to work out of box, only if given a chance. :)

Hope it helps understanding what we did.

---

