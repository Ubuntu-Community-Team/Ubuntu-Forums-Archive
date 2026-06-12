---
title: "Got WiFi working! Until I reboot..."
date: 2018-10-06
forum: Networking &amp; Wireless
---

### Post by gilbertusalbans on 2018-10-06
I am a linux noob...

Ubuntu 18.04.1 LTS
Intel Core&#8482; i5-6600K CPU @ 3.50GHz × 4 
TP-LINK Archer T4U USB WiFi adapter

When I installed Ubuntu it did not find the WiFi adapter. I got it working with a wired connection and:

sudo apt install rtl8812au-dkms

The adapter lit up and started working. However when I power cycle the machine it stops working. I have to hook up a network cable and run:

sudo apt --reinstall install rtl8812au-dkms

Any tips on how to get the changes to survive a power cycle?

Thanks in advance!

---

### Post by jeremy31 on 2018-10-06
Have you tried unplugging the wifi and plugging it back in after Ubuntu is loaded?
Or are you running Ubuntu from ISO, try without installing?

---

### Post by gilbertusalbans on 2018-10-06
Thanks for your reply.

I have Ubuntu installed, not running from ISO.

It did try unplugging and plugging back in the adapter.  It did not work without hooking up a wired connection and reinstalling the driver. Although that was on 17.10 before I upgraded to 18.04. I can try it again if upgrading is likely to have made a difference.

---

### Post by jeremy31 on 2018-10-06
See the wireless script link in my signature and post results

---

### Post by gilbertusalbans on 2018-10-06
That's pretty slick. :)

[http://paste.ubuntu.com/p/5V5HBvFvdt/](http://paste.ubuntu.com/p/5V5HBvFvdt/)

---

### Post by gilbertusalbans on 2018-10-06
I rebooted (needed to install a new drive anyway). 

WiFi adapter did not come back up.

Tried unplugging and reconnecting the WiFi adapter. No luck.

I hooked up the network cable and re-ran the wireless script with the WiFi adapter still not functioning.

[http://paste.ubuntu.com/p/RFHrf2w7Mt/](http://paste.ubuntu.com/p/RFHrf2w7Mt/)

I'm hoping that comparing this one to the link above (where the WiFi is working) will show something useful.

I reinstalled the driver and got this output:

```
[FONT=courier new]$ sudo apt --reinstall install rtl8812au-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  golang-1.8 golang-1.8-doc golang-1.8-go golang-1.8-src libssl-doc
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,116 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 rtl8812au-dkms all 4.3.8.12175.20140902+dfsg-0ubuntu8 [1,116 kB]
Fetched 1,116 kB in 1s (1,035 kB/s)       
(Reading database ... 291297 files and directories currently installed.)
Preparing to unpack .../rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb ...


-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  4.15.0-33-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


8812au.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  4.15.0-34-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


8812au.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...


DKMS: uninstall completed.[/FONT]


-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  4.15.0-36-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


8812au.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 4.3.8.12175.20140902+dfsg
completely from the DKMS tree.
------------------------------
Done.
Unpacking rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu8) over (4.3.8.12175.20140902+dfsg-0ubuntu8) ...
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu8) ...
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Progress: [ 67%] [######################################....................] 
Progress: [ 67%] [######################################....................] 
Done.ess: [ 67%] [######################################....................] 


8812au:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-36-generic/updates/dkms/


depmod...


DKMS: install completed.
$

```

Oddly, the adapter did not come back up this time.

I unplugged it and plugged in back in again and it still did not work.

I plugged it into a different USB port and it worked.

I'm so confused. :)

---

### Post by jeremy31 on 2018-10-07
Something is happening with the USB ports, try a reboot without the wifi plugged in

---

