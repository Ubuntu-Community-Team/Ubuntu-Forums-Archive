---
title: "Netgear ac6100 wifi adapter not detected."
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by mcmiste2 on 2016-12-07
Hi guys/gals. I've just installed ubuntu studio 16.04 on my pc and can't seem to get the wifi adapter to become detected. Adapter is netgear ac6100. I've done some searching and it looks like the solution in this link  [http://www.humans-enabled.com/2016/03/how-to-ubuntu-1604-gnu-linux-netgear.html?m=1](http://www.humans-enabled.com/2016/03/how-to-ubuntu-1604-gnu-linux-netgear.html?m=1) is probably what I need to do, however.... 

 I can't get past the first step. I get this message " Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/) , is another process using it? " after inputting the command in the first step. Any help is much appreciated, danka.

---

### Post by wildmanne39 on 2016-12-07
Make sure you have only the terminal open when running the commands, you almost assuredly have software center or updater open too, so close all the software installers if that does not work reboot and that should clear the issue and then just open the terminal.

---

### Post by derekshaw on 2017-02-07
since the original poster left this as open (as is the only other thread I can find about this), and I have bumped up against this too (but gotten only a little bit farther).

This is what I have done in capsule format:
```
lsusb
  Bus 002 Device 005: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
  -> OK there is a dkms for that device in the repositories (https://ubuntuforums.org/showthread.php?t=2326038)
 apt install dkms   #(not already installed)
 wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
 dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
```
everything seemed to complete without error
rebooted, no wifi devices found
after a reboot lsmod shows the module is not loaded
modprobe 8812au successfully loads the module, but network manager can't see any wifi devices.

```
root@2013apr-01:~# lsmod | grep 88
nfsd                  319488  13

root@2013apr-01:~# modprobe 8812au

root@2013apr-01:~# lsmod | grep 88
8812au                905216  0
nfsd                  319488  13
```


I have run the wireless-info script as root (which showed me the 8812au module was not loadedafter boot ) and the results can be found here:
[http://paste.ubuntu.com/23949479/](http://paste.ubuntu.com/23949479/)

It would be really helpful if I could get the two of these dual-band adapters working with some machines we have here.

Thanks in advance!
d.

---

### Post by wildmanne39 on 2017-02-07
Please do:
```
sudo modprobe -v 8812au
sudo dpkg-reconfigure resolvconf
```
does it connect or try to connect? if not post a new wireless script while the driver is loaded meaning do not reboot first.
Thanks

---

### Post by derekshaw on 2017-02-09
> **wildmanne39 said:**
> Please do:
```
sudo modprobe -v 8812au
sudo dpkg-reconfigure resolvconf
```
does it connect or try to connect? if not post a new wireless script while the driver is loaded meaning do not reboot first.

Thanks for the help!

here's the output from the commands:
```
root@2013apr-01:~#  modprobe -v 8812au
insmod /lib/modules/4.4.0-62-generic/updates/dkms/8812au.ko 
root@2013apr-01:~# dpkg-reconfigure resolvconf
```

That seemed to make no operational difference. Network manager does not see any wi-fi devices. lsusb shows the device, lsmod shows the kernel module.

After executing the two commands, before doing anything else (per your request above)
[http://paste.ubuntu.com/23962625/](http://paste.ubuntu.com/23962625/)

after rebooting (per the resolvconf recommendation)
[http://paste.ubuntu.com/23963697/](http://paste.ubuntu.com/23963697/)

since we/re messing with resolvconf, I reversed an edit I made to NetworkManager.conf (to allow dnsmasq to be resolver), as part of the stock deployment process.

after my edit to NetworkManager.conf and a reboot.
[http://paste.ubuntu.com/23963748/](http://paste.ubuntu.com/23963748/)

So, if we're into the "probably not worth the effort", or "I'm too stubborn to give up" stage, I'd happily accept guidance for USB devices that work out of the box with Ubuntu 16.04.  Need to be dual-band.

Thanks again for all help!
d.

---

