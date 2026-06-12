---
title: "acerhk Ubuntu 14.04 TravelMate 292"
date: 2015-02-01
forum: Networking &amp; Wireless
---

### Post by ZioAlfredo on 2015-02-01
[http://ubuntuforums.org/showthread.php?t=1708093](http://ubuntuforums.org/showthread.php?t=1708093)

Hi,
I have the same problem of the above post.
How do I make the kernel module for Ubuntu 14.04?

Thank you very much!

Tried the acerhk GUI but with no success...

Edit: I have found a solution!
It consists in downloading the package: [https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk](https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk)
and compiling it as follows:
become root:
```
sudo su
```

go to the acerhk path:
```
cd /usr/src
```

extract the acerhk-source:
```
tar -xjf acerhk.tar.bz2
```

After extracting you have to change to:
```
cd /usr/src/modules/acerhk
```

compile acerhk-module:
```
make
```
(maybe compiling fails with the latest kernel in 14.04 cause something changed in kernel >3.13 and i am not sure if it is backported - so if it fails please send me the console output)

copy the module to another directory:
```
cp acerhk.ko /lib/modules/$(uname -r)/kernel/ubuntu/
```

register module for the kernel:
```
depmod -A
```

load the module:
```
modprobe acerhk force_series=290 usedritek=1 verbose=5
```
(i think there are 3 verbose-levels, so verbose=5 gives us all output on dmesg)

activate the wireless-adapter (its not just the led, its the whole adapter):
```
echo 1 > /proc/driver/acerhk/wirelessled
```

In order to enable automatically acerhk at startup, edit file:
```
/etc/init.d/rc.local
```

and append the following two lines at the end of it:
```
modprobe acerhk force_series=290 usedritek=1 verbose=5
echo 1 > /proc/driver/acerhk/wirelessled
```

---

### Post by Ben_K._D._Pearce on 2015-09-05
Thank you kindly!

I initially couldn't enable the hardware-disabled wifi on my Acer Aspire ES 15 running Ubuntu 14.04.
Your solution worked perfectly!

The hardware re-disables wifi upon shutdown or sleep, so I added a few lines to my .bashrc so I could enable it by opening a terminal (ctrl + alt + t)

```

rfkill list | if grep "Hard blocked: yes"; then
   echo "Enabling Wifi"
   modprobe acerhk force_series=290 usedritek=1 verbose=5
   echo 1 > /proc/driver/acerhk/wirelessled
fi

```

---

