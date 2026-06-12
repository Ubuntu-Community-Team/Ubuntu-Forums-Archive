---
title: "Problem with network configuration on UBUNTU Server 12.04 LTS"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by Theo Molenaar on 2013-11-19
Hi, 

All in a sudden I have a problem with the network configuration on my 12.04 LTS server. During booting the following is shown:

Waiting for server network configuration...
Waiting up to 60 more seconds for network configuration...
Booting system without full network configuration...

File /etc/network/interfaces looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254

The server worked fine for the last 9 months and the configuration of /etc/network/interfaces has not been changed. As far as I am aware, no packages have been installed recently. 

Noteworthy is that I recently compiled a specific version for the Realtek NIC. Reason: to get around problems with wakeonlan/etherwake, which did not work anymore after an update of the Realtek driver. this seems to be an old problem which is not still not fixed. See [here]("http://ubuntuforums.org/showthread.php?t=2042675") for more details. 
The driver I installed is version r8168-8.035.00, and in /etc/modprobe.d/blacklist.conf I added these lines: 

# old RealTek network driver
blacklist r8169

This was 3 weeks ago and the network worked fine for 2 weeks. Since then the network cannot be configured anymore, as indicated above.

Any help is appreciated!
Thanks,
Theo

---

### Post by praseodym on 2013-11-19
Did you install a GUI?

---

### Post by Theo Molenaar on 2013-11-20
No, no gui installed.

---

### Post by steeldriver on 2013-11-20
anything useful in dmesg?

```
dmesg | grep eth0
```

---

### Post by chili555 on 2013-11-20
Have you had a kernel update? Remember, you must re-compile r8168 for each new kernel.

---

### Post by Theo Molenaar on 2013-11-20
The output of 'dmesg | grep eth0' is none.

Kernel update: I am not sure. How can I investigate this? The server is used as a backup server. Normally it is shut down, once a week it is woken up via etherwake to perform a backup of my NAS. After finishing (normally 3-4 hours) it shuts itself down again. Automatic updates are turned on, but if a kernel update took place, it could only have been done in this 3-4 hour slot.

Edit: uname -a gives this:
Linux Mollux7 3.5.0-43-generic #66~precise1-Ubuntu SMP Thu Oct 24 14:52:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
So the kernel has been updated recently. I wil try recompiling the driver and see if that works.

---

### Post by chili555 on 2013-11-20
> The output of 'dmesg | grep eth0' is none.Meaning that no driver attached to the hardware and created an interface eth0. 

When you compile a driver or, for that matter, anything else, from source code, it is compiled against your currently running kernel only. When automatic updates installs a newer kernel, it doesn't contain the driver so you need to re-compile. Whenever you reboot, the boot goes to the latest kernel; i.e. the one without the driver. 

You can troubleshoot the quick way with:```
sudo modprobe r8168
```If you get this:```
FATAL: Module r8168 not found.
```...then you know what happened and that you need to recompile:```
cd Downloads/r8168-8.035.00  [COLOR="#FF0000"]<--or wherever it is[/COLOR]
make clean
make
sudo make install
sudo modprobe r8168
```If this is a production server, I'd either turn off automatic updates and update and re-compile manually, or I might conjure up a little script and drop it into /etc/rc.local to re-compile at every reboot. There is probably some way to do it with DKMS, but that is outside my area of expertise.

---

### Post by Theo Molenaar on 2013-11-20
I recompiled the r8168 driver and that did the trick. Thanks chili555  for putting me on the right track, your my hero!

One final question: how can I turn off automatic updates, just to be sure that in the future I do not run into the same problem again?

---

### Post by Theo Molenaar on 2013-11-20
I recompiled the r8168 driver and that did the trick. Thanks chili555  for putting me on the right track, your my hero!

One final question: how can I turn off automatic updates, just to be sure that in the future I do not run into the same problem again?

---

### Post by houstonbofh on 2013-11-20
A better solution is to replace that nic.  I will not go into all of the reasons I hate realtek nics, but if you replace it with a cheap Intel nic from eBay, you will get better performance, and you will not need a custom compiled driver.  Just not doing updates is a poor option in my mind.

---

### Post by chili555 on 2013-11-20
Glad it's working. Please see: [http://askubuntu.com/questions/172524/how-can-i-check-if-automatic-updates-are-enabled](http://askubuntu.com/questions/172524/how-can-i-check-if-automatic-updates-are-enabled)

I would only forgo automatic updates if you intend to log on to the machine fairly frequently to do them yourself. I believe there is a mechanism to blacklist certain packages from automatic updates; for instance linux-image and linux-headers.

As inexpensive as NICs are, I'd research a replacement, too.

---

### Post by Theo Molenaar on 2013-11-20
Thanks guys for all the help and advices! I will surely consider a replacement of the NIC as the Realtek has caused me quite some headaches already.

Thanks, Theo

---

