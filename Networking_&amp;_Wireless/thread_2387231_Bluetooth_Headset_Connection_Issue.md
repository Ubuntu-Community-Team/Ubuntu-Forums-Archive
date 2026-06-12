---
title: "Bluetooth Headset Connection Issue"
date: 2018-03-16
forum: Networking &amp; Wireless
---

### Post by adventure man on 2018-03-16
Hey guys, I recently bought a bluetooth headset for my laptop but can't seem to connect them and receive errors.

Some Specs:
Lubuntu 17.04 Zesty
Acer Aspire V5 Laptop
Treblab XR100 Headset 

What happens is, I turn on the "BlueTooth Manager" program, click pair and 3 blue, green and orange indicators come up but after a few seconds disappear. So I run the setup assistant in the same program and try to set it up as a "headset". After it seems to set things up and I hear a tone in my headset I get the error "**Device added successfully, but failed to  connect**".

As a last resort I attempt again by clicking at the top of the Bluetooth Devices box options: Device -> Headset and get this error at the bottom of the Bluetooth Manager box:

"**Connection Failed: blueman.bluez.errors.DBusFail**"


*I've tried a few fixes that I've found in searches but I always get the same error.

The headset works perfectly with my tablet, phone (Android 5) and on Windows 7,10.


Any advice?

---

### Post by jeremy31 on 2018-03-16
I think that happens when the module-bluetooth-discover is not loaded in pactl, check in terminal with ```
pactl list short | grep module-bluetooth
```

---

### Post by adventure man on 2018-03-16
> **jeremy31 said:**
> I think that happens when the module-bluetooth-discover is not loaded in pactl, check in terminal with ```
pactl list short | grep module-bluetooth
```

Is that the correct code? I copy it into terminal and do not get anything.  Retried with headset after and get the same problem.

It just comes unpaired after a few seconds.

---

### Post by jeremy31 on 2018-03-16
That means no module-bluetooth-discover is loaded, do
```
pactl load-module module-bluetooth-discover
```
Then reconnect to the headset

---

### Post by adventure man on 2018-03-16
> **jeremy31 said:**
> That means no module-bluetooth-discover is loaded, do
```
pactl load-module module-bluetooth-discover
```
Then reconnect to the headset


ah ok, I tried the new code above and got this error:  "**Failure: Module initialization failed**"
I also must add that I have tried in the past another extra USB Wireless Bluetooth CSR 4.0 Dongle Adapter (which I use on my Windows PC) with the same results as my laptop's onboard bluetooth.

---

### Post by jeremy31 on 2018-03-16
I would try ```
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover
```

---

### Post by adventure man on 2018-03-16
> **jeremy31 said:**
> I would try ```
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover
```

Thanks for all the help jeremy.  I have tried this is the past and I can't seem to connect to get the download but it seems I am missing this bluetooth module.  Here is what terminal read out when I popped that code in:
 
**The following NEW packages will be installed:**
**  pulseaudio-module-bluetooth**
**0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.**
**Need to get 56.9 kB of archives.**
**After this operation, 294 kB of additional disk space will be used.**
**Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/main amd64 pulseaudio-module-bluetooth amd64 1:10.0-1ubuntu2**
**  404  Not Found [IP: 91.189.91.26 80]**
**E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_10.0-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_10.0-1ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.26 80]**
**E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?**

---

### Post by jeremy31 on 2018-03-16
That is why you get an error, 17.04 isn't supported anymore

---

### Post by adventure man on 2018-03-16
Thanks jeremy I upgraded to 17.10, redid everything we talked about in this thread and got my headset working.

---

### Post by jeremy31 on 2018-03-16
After you disconnect you might need help getting audio again, I use the a2dp.py script, [https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae](https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae)
I think you need to edit the first line to use python 3.6

---

