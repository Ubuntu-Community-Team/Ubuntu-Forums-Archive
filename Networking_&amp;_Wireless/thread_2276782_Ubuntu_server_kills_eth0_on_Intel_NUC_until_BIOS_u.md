---
title: "Ubuntu server kills eth0 on Intel NUC until BIOS update, then dead again after reboot"
date: 2015-05-04
forum: Networking &amp; Wireless
---

### Post by pat27 on 2015-05-04
I have an Intel NUC model DC53427HYE with an Intel 82579LM onboard LAN, that uses the E1000e driver.

This has been happily running as a headless server for about 2 years, most recently on ubuntu server 14.04.2. I updated the server using ```
apt-get update/upgrade
``` + a restart about a month ago with no problems, and today did the same routine, also installing ```
ethtool
``` and then performing a shutdown to move some shelving around in my closet where the NUC resides.

On restarting the NUC, which is my network's DHCP server, I noticed it was not appearing on the network. I did some debugging, and discovered that eth0 was no longer showing up. ```
lspci
``` and ```
dmesg
``` had no references to eth0 (or any other eth device), and the network lights on the physical unit were off.

I attempted to install new Intel drivers, going to version 3.1.0.2-NAPI from Intel's site. I also removed ethtool to no avail. In desperation, I tried installing a new firmware/BIOS on the NUC, and was happy to see eth0 returned and all appeared well. However, when I shutdown the NUC and returned it to my server "closet," eth0 was again (cue Doc Brown voice) "erased, erased from existence!"

I've tried all manner of troubleshooting, but the only way to restore eth0 is to update the NUC firmware, overwriting with the same version. Once I shutdown Ubuntu or reboot, eth0 acts like it doesn't exist.

Any ideas?

---

### Post by chili555 on 2015-05-05
> lspci and dmesg had no references to eth0 (or any other eth device), and the network lights on the physical unit were off.Let's have a look:```
lspci -nn | grep 0200
```What happens when you try to manually load the driver?```
sudo modprobe e1000e
```Any errors or warnings at the terminal when you loaded it? Any clues here?```
dmesg | grep e100
```When you ran lspci, if the device shows up, what is the PCI bus number? Here is an example:```
[COLOR="#FF0000"]00:19.0[/COLOR] Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
```Check dmesg for the bus number you found; in my example:```
dmesg | grep 00:19.0
```

My NUC, also using e1000e, works perfectly, so we can do some comparisons.

My initial suspicion is that it's a BIOS setting.

---

### Post by pat27 on 2015-05-05
Thanks so much for the reply, especially helping a fellow South Carolinian :-)

Here are the results AFTER a NUC firmware update that restores ethernet functionality:

```
lspci -nn | grep 20000:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)

```

```
sudo modprobe e1000e
<nothing returned>
```

```
dmesg | grep e100[    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
[    2.168851] e1000e: module verification failed: signature and/or  required key missing - tainting kernel
[    2.196718] e1000e: Intel(R) PRO/1000 Network Driver - 3.1.0.2-NAPI
[    2.198587] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    2.200945] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.202943] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    2.408169] e1000e 0000:00:19.0 eth0: registered PHC clock
[    2.408184] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) ec:a8:6b:f9:94:8b
[    2.408185] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.408234] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    9.260359] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    9.364299] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   12.947523] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None



```

Only thing that really looks interesting is the second line about the missing key, but this doesn't prevent eth0 from coming up (again, only after a NUC BIOS/firmware update [not sure what they call it these days, in my day is was "flashing the BIOS"].

```
dmesg | grep 8086:1502[    0.176972] pci 0000:00:19.0: [8086:1502] type 00 class 0x020000

```

I'll do another post after rebooting with the above, but again, this is the state of the system on the first boot after a BIOS flash, using the most current version and basically "over flashing" the exact same version.

---

### Post by pat27 on 2015-05-05
Here's the state of the system after a simple shutdown. Again, nothing changed physically with the device other than moving back to the server closet where it is only connected to power and ethernet, a configuration that worked fine for the last ~2 years before I did an at-get update/upgrade and installed ethtool. Only command issued after capturing the above was a:
 
```
sudo shutdown -h now
```
 
After booting (with a few network-related errors like "waiting for network configuration") the above diagnostics result in:
 
```
lspci -nn | grep 0200
<nothing returned>

```
 
```
sudo modprobe e1000e
<nothing returned>

```
 
```
dmesg | grep e100
[ 173.824172] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[ 173.824175] e1000e: Copyright(c) 1999 - 2013 Intel Corporation

```
 
Interesting that this last line makes it appear that an old driver is being loaded. I wonder why the BIOS update causes the new one to load? Event with e1000e appearing, I still cannot successfully perform an "ifup eth0".

After re-flashing the BIOS (again to same exact version), I'm back up and running.

---

### Post by chili555 on 2015-05-05
Usually, the driver version reverts when a reboot is into a later kernel version. In other words, you compiled against 3.16.0-42 or some such, and updated to 3.16.0-43. Upon reboot, the default driver included in x-43, 2.3.2-k, loads. It's easy to fix but useless if the device doesn't actually even show up!!!> lspci -nn | grep 0200
<nothing returned>> a fellow South Carolinian Where, if I may ask? I am across the lake from Charlotte.

I am leaving for an appointment in just a few moments, but will reboot my NUC so I can look around the BIOS when I return in a while. I will note all my non-default settings in case they are helpful to you. 

Very interesting problem we have here.

---

### Post by pat27 on 2015-05-05
> **chili555 said:**
> Usually, the driver version reverts when a reboot is into a later kernel version. In other words, you compiled against 3.16.0-42 or some such, and updated to 3.16.0-43. Upon reboot, the default driver included in x-43, 2.3.2-k, loads. It's easy to fix but useless if the device doesn't actually even show up!!!Where, if I may ask? I am across the lake from Charlotte.

I am leaving for an appointment in just a few moments, but will reboot my NUC so I can look around the BIOS when I return in a while. I will note all my non-default settings in case they are helpful to you. 

Very interesting problem we have here.

It's especially frustrating since this little NUC has been sitting happily doing it's thing, until I decided to move some shelving around in the closet where it "lives."

I'm right across from Charlotte as well, in fabulous Fort Mill.

---

### Post by chili555 on 2015-05-05
Fabulous Ft. Mill! Mrs. Chili and I were there for lunch a couple of weeks ago at the fabulous Flipside. 

Here are the settings I changed from defaults or at least reviewed in the BIOS. They may or may not be helpful:

*Legacy boot
*SATA configuration AHCI
*Onboard devices: audio, HDMI and, of course, LAN
*PCI latency 32  
*Add in configuration - no changes  <---all of it is, on my NUC, related to LAN; I could see nothing to change that seemed helpful
*Power > Secondary Deep S4/S5 selected and also ASPM enabled

I had a problem when I first acquired my NUC where, when I selected 'shut down' in the operating system, it immediately restarted. I read on Intel's NUC forum to try Deep S4/S5, whatever that is, and it solved my issue.

Is your reloaded BIOS just set to defaults or what?

I am still mystified that the device just completely disappears.

---

