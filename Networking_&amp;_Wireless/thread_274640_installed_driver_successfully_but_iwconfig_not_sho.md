---
title: "installed driver successfully but iwconfig not showing wlan0"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by bithika_mookherjee on 2006-10-10
Hi,

There are a lot of threads about the belkin USB FD57050, but I can't seem to find the answer to this particular problem. I am relatively new to Linux (and totally new to Ubuntu!).

I'm using Ubuntu 6.06 - I managed to install the driver for the Belkin USB FD57050, via these steps:

```
sudo ndiswrapper -i rt73.inf
```

typing,
```
sudo ndiswrapper -l
```

when my USB is plugged in, returns 
```
rt73 driver present, hardware present
```

then I configured the ndiswrapper module to load at boot via:
```
sudo ndiswrapper -m
```

and all that seems OK.

I am following a HOWTO called "Easy-Peasy Wireless" written by Csar:
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux) 

He suggests that after configuring the ndiswrapper module, that 
I type:

```
sudo ndiswrapper -hotplug
```

This is where it goes wrong, as ndiswrapper just returns a list of available flags as though "-hotplug" was not a valid option.
I googled "hotplug" and it seems that this is something the kernel calls to when detecting plug and play devices. I guess thi s response from ndiswrapper means I don't have "hotplug"? 

Also,
```
sudo iwconfig
```
does not display wlan0 although my hardware is shown as present in "System Devices".

Has anyone encountered that "-hotplug" problem before - should I download it or is there an alternative with Ubuntu 6.06?
Any suggestions on how to proceed from here?

Best Wishes
Bithika

---

### Post by joergenlie on 2006-10-11
Try:
sudo ndiswrapper -i xx.inf (your .inf file)
sudo ndiswrapper -l (hardware driver present)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

if ndiswrapper doesn't load at startup add "ndiswrapper" at the end of     /etc/modules

Jørgen

---

### Post by bithika_mookherjee on 2006-10-16
hi,
Thanks for the reply.

I tried out the steps you sent exactly and added ndiswrapper to the end of /etc/modules but no luck however. iwconfig does not report a wlan0, although my hardware and my driver is present.

I tried running "sudo ndiswrapper -hotplug" again, but I still got the same message - what is hotplug and do I need it?

I'm totally stuck at this point - any help much appreciated.

Best Wishes
Bithika

---

