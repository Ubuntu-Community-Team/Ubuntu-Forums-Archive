---
title: "[SOLVED] forcedeth -&gt; eth0: too many iterations (6) in nv_nic_irq"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by jakethecake on 2008-08-10
I only found archived threads regarding this kernel warning; 
"eth0: too many iterations (6) in nv_nic_irq."

I'm recreating a thread about this warning, because the solution procedure has changed a little. 

Config file location for modprobe is now different than with Gutsy/Feisty. Putting options in /etc/modprobe.conf or in /etc/modprobe.d/yourconfig.modprobe does not work anymore, the 'update-modules' command is depreciated. 

My setup is Ubuntu 8.04.1 with the latest stable kernel right now; 2.6.24-20-generic. And I get this error when streaming large files via NFS.

To correct warning, just add: 
"options forcedeth max_interrupt_work=20" to '/etc/modprobe.d/options'. 

The nvidia forcedeth module will then on boot get your options and not hit the interrupt limit. 

If you still get messages that look like this;
"eth0: too many iterations (21) in nv_nic_irq."

Then just increse max_interrupt_work to something higher, say 200. 
(and read [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/130075](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/130075))

---

### Post by rbm0307 on 2008-10-02
Jake,

Thanks for your timely post.  I've been experiencing mysterious LIRC hangs on my Mythtv frontend and I think I have narrowed it down to this bug with nVidia ethernet on my Mythtv backend.

I tried your solution above (along with other proposed solutions previously posted here on the forums) but I still receive the message:

"eth0: too many iterations (6) in nv_nic_irq."

when playing a stored video in Myth. Reason is that large NFS file transfers when playing videos trigger this bug on my backend.  The result is, as I mentioned, LIRC hangs on the frontend.

My backend is new for me.  It's an ASUS M2N-SLI Deluxe with an AMD Athlon 64bit X2 dual core 5000+, 2GB DDR2 memory, Ubuntu 8.0.4 with 2.6.24-19 kernel, MythTV 0.21+fixes18259. Here is output from "dmesg", "lspci -vvnn" and "uname -a".

Obviously, from the message I am receiving, the "options forcedeth max_interrupt_work=20" line I've put into /etc/modprobe.d/options is not working.  If it was, I would have expected a (21), not a (6) in the error message.

So, what am I doing wrong?  What command will allow me to view the currently set value for max_interrupt_work variable in the forcedeth module?

Thanks in advance for any assistance. (Urgent as the WAF is negative at the moment and there are rumblings to get a "real TV" from SWMBO).

Robert.
[ATTACH]87091[/ATTACH]

---

### Post by jakethecake on 2008-10-03
Executed, these commands and paste it's output here.

modprobe -c |grep forcedeth |wc -l
lsmod |grep forcedeth
cat /etc/modprobe.d/options
modprobe -l |grep force 
grep forcedeth /var/log/syslog
grep forcedeth /var/log/dmesg
grep forcedeth /var/log/udev

---

### Post by rbm0307 on 2008-10-03
modprobe -c |grep forcedeth |wc -l
```
40
```
lsmod |grep forcedeth
```
forcedeth   55564  0
```
cat /etc/modprobe.d/options
```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# saa7134
options saa7134 card=39 tuner=2

# fix Nvidia ethernet interrupt overrun
options forcedeth max_interrupt_work=20
```
modprobe -l |grep force
```
/lib/modules/2.6.24-19-generic/kernel/drivers/i2c/busses/i2c-nforce2.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/input/joystick/iforce/iforce.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko
```
grep forcedeth /var/log/syslog
```
Oct  2 05:34:25 mythbe kernel: [   21.207728] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Oct  2 05:34:25 mythbe kernel: [   21.727856] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:60:4b:26:46
Oct  2 05:34:25 mythbe kernel: [   21.727860] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Oct  2 05:34:25 mythbe kernel: [   22.247802] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1d:60:4b:42:ca
Oct  2 05:34:25 mythbe kernel: [   22.247806] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
Oct  2 05:34:39 mythbe NetworkManager: <info>  eth1: Device is fully-supported using driver 'forcedeth'. 
```
grep forcedeth /var/log/dmesg
```
[   21.207728] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   21.727856] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:60:4b:26:46
[   21.727860] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   22.247802] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1d:60:4b:42:ca
[   22.247806] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
```
grep forcedeth /var/log/udev
```
UEVENT[1222940056.186760] add      /bus/pci/drivers/forcedeth (drivers)
DEVPATH=/bus/pci/drivers/forcedeth
UDEV  [1222940056.201715] add      /bus/pci/drivers/forcedeth (drivers)
DEVPATH=/bus/pci/drivers/forcedeth
DRIVER=forcedeth
DRIVER=forcedeth
DRIVER=forcedeth
DRIVER=forcedeth
```
Cheers.
Robert.

---

### Post by jusmop on 2009-03-10
I've added "options forcedeth max_interrupt_work=20" to '/etc/modprobe.d/options' without success.

I still get the same message:
"eth0: too many iterations (6) in nv_nic_irq.".

Yes, with (6) not (20). How can I check that the max_interrupt_work option is actually being set?

Environment: Ubuntu Intrepid 32 bit (2.6.27) running on an Asus M2NPV-VM (Nvidia GeForce 6150 + nForce 430) with a AMD Athlon 4850e dual core CPU.

These messages only came up after upgrading my network switch to a gigabit model AND when transferring large files across the network (using MythTV).

---

### Post by jusmop on 2009-03-10
Forgot one important detail: there is no loss in network data transfer, but I have no idea if the network is working as well as it should (otherwise why would there be the error message?).

---

