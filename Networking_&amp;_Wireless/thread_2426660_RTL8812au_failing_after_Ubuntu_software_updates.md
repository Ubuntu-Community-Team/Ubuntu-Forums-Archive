---
title: "RTL8812au failing after Ubuntu software updates"
date: 2019-09-12
forum: Networking &amp; Wireless
---

### Post by bosstiat on 2019-09-12
I guess one of the recent Ubuntu 18.04 patches upgraded the kernel to 5.0.0-27-generic and my wifi all of a sudden stopped working after dinner. I had tried Ubuntu 19.04 already and my wifi never worked there even on a clean install (IIRC). So now that I am in the middle of a few projects, I would really like my wifi to work again.

I have the following adapter: [https://www.amazon.com/EDUP-ac600Mbps-Wireless-External-10-6-10-13/dp/B01CCMUN8C](https://www.amazon.com/EDUP-ac600Mbps-Wireless-External-10-6-10-13/dp/B01CCMUN8C)
I believe the issue is with driver RTL8812au and dkms, but I am not a networking person at all and don't really know why it stopped working after a OS update.

I was previously getting [COLOR=#000000] 8812au: version magic '5.0.0-25-generic SMP mod_unload ' should be '5.0.0-27-generic SMP mod_unload ' in /var/log/syslog.[/COLOR]
I tried the steps here to no avail: [https://ubuntuforums.org/showthread.php?t=2412895](https://ubuntuforums.org/showthread.php?t=2412895) (replacing it kernel 5.0 stuff). However, that message doesn't appear anymore.

Currently my dkms status says the following:
nvidia....
nvidia....
nvidia....
rtl8812au, 4.38.12165.201409002+dfsg, 4.15.0-58-generic, x86_64: installed
rtl8812au, 4.38.12165.201409002+dfsg, 4.15.0-62-generic, x86_64: installed
rtl8812au, 4.38.12165.201409002+dfsg, 5.0.0-25-generic, x86_64: installed
rtl8812au, 4.38.12165.201409002+dfsg, 5.0.0-27-generic, x86_64: installed (WARNING! Diff between built and installed module!)

---

### Post by jeremy31 on 2019-09-13
Try ```
wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu10_all.deb
sudo dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu10_all.deb
```
Reboot

---

### Post by bosstiat on 2019-09-15
Worked by running this code @jeremy31 on reboot. Thank you very much. 

Let me know if you would like logs from anywhere.

---

### Post by scuba707 on 2019-12-05
Hope this works for v16.04LTS Xenial also...
I've been waiting for over a year now for a patch for my ALFA
twin-RF USB Dongle.  Have two WiFi Antennas on top of my
truck that have been useless since this module broke...

---

### Post by jeremy31 on 2019-12-05
scuba707, if you have already installed rtl8812au-dkms, do ```
gedit admin:///usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```
Replace ```
MAKE="'make' all"
```
With ```
MAKE="'make' all KVER=${kernelver}"
```
Then try ```
sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
```
See if any errors occur

---

### Post by scuba707 on 2020-03-09
Module rtl8812au/4.3.8.12175.20140902+dfsg already installed on kernel 4.15.0-88-generic/x86_64

---

### Post by scuba707 on 2020-03-09
couldn't find the DELETE button to get rid of this dupe

---

### Post by scuba707 on 2020-03-09
This just started happening about the time the ALFA Dongle started failing.
I'm getting systemd module load failure errors, at least a couple dozen, on boot sequence.
The 'system status...' inquire responds with:

===
&#9679; systemd-modules-load.service - Load Kernel Modules
   Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2020-03-09 11:37:23 PDT; 9min ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 1508 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=1/FAILURE)
 Main PID: 1508 (code=exited, status=1/FAILURE)

Mar 09 11:37:23 pinetree systemd[1]: Starting Load Kernel Modules...
Mar 09 11:37:23 pinetree systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Mar 09 11:37:23 pinetree systemd[1]: Failed to start Load Kernel Modules.
Mar 09 11:37:23 pinetree systemd[1]: systemd-modules-load.service: Unit entered failed state.
Mar 09 11:37:23 pinetree systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
===

Could this is some way be preventing the 8812au module from being loaded ?
I have tried loading the module manually (tainting the kernel), get no errors,
but whenever the Dongle is plugged in all WiFi networking is killed.
It WAS working fine, and I could pull down NIC list and disconnect the built-in,
and the USB NIC would take over connection.
I can be running along fine from a fresh boot (no dongle inserted), but then
when plug in the dongle it knocks out the internal NIC also.
Nothing gets it working again but removal of the usb, and cold reboot.
Then the internal is working again.  But I really need the external antennas.

---

