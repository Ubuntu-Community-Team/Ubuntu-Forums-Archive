---
title: "eth0:  Device not found"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by jefrat72 on 2006-08-24
I used G4U to ghost an existing Ubuntu 6.06 Server to another physical machine.  They are both Dell Optiplex GX620s, however the first machine was a mini-tower 3.2Ghz and the 2nd machine is a 2.8Ghz tower.  

After ghosting to the tower Ubuntu Server booted up just fine, however I get this error when I enter command ifconfig eth0:

"eth0: error fetching interface information: Device not found"

If I do command modprobe eth0:

"FATAL: Module eth0 not found"

I have also run dmesg and did see the ethernet card listed.  But I'm stuck, how can I get the tower to recognize eth0 again?

---

### Post by ielliott on 2006-08-24
I'm having the same problem through a VMWare'd Ubuntu

---

### Post by ielliott on 2006-08-24
I just did (when i say it)

Sudo ifup eht0 and it worked you should try that.

---

### Post by jefrat72 on 2006-08-24
Thanks but I still get an error:

SIOCSIFADDR: No such device
eth0: Error while getting interface flags:  No such device
eth0: Error while getting interface flags:  No such device
Bind socket to interface: No such device
Failed to bring up eth0

---

### Post by newlinux on 2006-08-24
what does plain old 
```
ifconfig
```
return? Maybe you have nothing mapped to eth0. I've seen some systems start off at eth1 or eth2 by default. Not sure why. But you can change this if you want. dmesg may have already told you it is on eth0, but I'm not sure of what dmesg outputs (and I'm not on my ubuntu system right now to test), but I'm pretty sure ifconfig will show you what network devices are mapped to.

---

### Post by jefrat72 on 2006-08-24
ifconfig just brings up the loopback and my vmnet cards.

---

### Post by Iowan on 2006-08-24
If eth0 is an onboard adapter, might it be disabled in the BIOS?

---

### Post by jefrat72 on 2006-08-24
No, it's enabled.

---

### Post by cat5 on 2006-08-24
you should post the output of 
```
lspci
```
as well as 
```
lsmod
```

This will show us what modules are loaded, and what is actually seen. You 2 computers, as similar as they are, may have different NIC's, which would require a little tweaking of the driver, and a good old 'depmod -ae'

---

### Post by jefrat72 on 2006-08-24
Will do Cat5, however it won't be until Monday.  I'm off work till then.:D

Thanks.

---

### Post by jefrat72 on 2006-08-28
lsmod:

Module                  Size  Used by
vmnet                  62104  12 
vmmon                 165652  0 
ipv6                  327296  14 
af_packet              42252  0 
dm_mod                 69704  1 
md_mod                 83192  0 
lp                     22208  0 
pcspkr                 10760  0 
parport_pc             47856  1 
parport                50700  2 lp,parport_pc
tg3                   113284  0 
psmouse                47492  0 
serio_raw              16900  0 
snd_intel8x0           45224  0 
snd_ac97_codec        117180  1 snd_intel8x0
snd_ac97_bus           11136  1 snd_ac97_codec
snd_pcm_oss            66080  0 
snd_mixer_oss          27520  1 snd_pcm_oss
snd_pcm               110984  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              35592  1 snd_pcm
hw_random              14240  0 
snd                    74080  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              19872  1 snd
snd_page_alloc         21136  2 snd_intel8x0,snd_pcm
intel_agp              34744  1 
shpchp                 58272  0 
pci_hotplug            38800  1 shpchp
evdev                  21632  0 
tsdev                  17408  0 
sg                     50736  0 
usbhid                 49952  0 
ext3                  151824  1 
jbd                    72872  1 ext3
ide_generic             9984  0 
ehci_hcd               41480  0 
uhci_hcd               43424  0 
usbcore               152124  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 28416  3 
ata_piix               20740  4 
libata                 93088  1 ata_piix
scsi_mod              166904  3 sg,sd_mod,libata
ide_cd                 42912  0 
cdrom                  48184  1 ide_cd
piix                   20996  1 
generic                14340  0 
thermal                23692  0 
processor              37128  1 thermal
fan                    13576  0 
capability             14344  0 
commoncap              16896  1 capability
vga16fb                22288  1 
cfbcopyarea            12288  1 vga16fb
vgastate               17536  1 vga16fb
cfbimgblt              11392  1 vga16fb
cfbfillrect            12928  1 vga16fb
fbcon                  49792  70 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10880  1 bitblit


lspci:

0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 945G Integrated Graphics Controller (rev 02)
0000:00:02.1 Display controller: Intel Corporation 945G Integrated Graphics Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

---

### Post by cat5 on 2006-08-28
The 'lspci' output does not show an VMnet adaptors, only
a broadcom card. I don't have any broadcom's myself, so I am unsure of the driver. Your /etc/modules.aliases file is
pointing eth0 to the wrong driver being loaded...

I not at work either at the moment, so I can not verify which
drive you would need. Google?

---

### Post by scmerisina on 2006-09-03
I am a fairly experienced Linux person, but this problem has stumped me so far.  I have read all the posted messages in this thread, and I think they are NOT on a track to find a solution.

I my opinion, the problem is due to "ghosting".  I used UDPcast, not g4u.  

I cloned a lab full of identical machines (25) from a working "Golden Client" fully verified to be "good".  The clones booted fine, but in the clones eth0 is not found.  The relevant NIC is module is loaded; dmesg, lsmod, cat /proc/modules, lspci, etc show proper things corresponding to this NIC. Just to be sure, I rmmod it and reload it (modprobe -v ...), and reassuring messages show up in /var/log/dmesg.  But ifconfig eth0 gives the "error fetching interface information".  Of course, /proc/interrupts on the clone does not show eth0; the golden client shows it with an IRQ of 209.

I am deliberately not giving info regarding the specific NIC, the Ubuntu version, etc.  Let me just add that the hw did not go haywire after cloning.  I booted several of the clones with a LiveCD, and all are fine including the NICs.

If any of you have insights into this: How a raw image, entire disk to disk, cloning causes this problem so that the machine fails in dhcp but the rest is OK.  I am wondering if the recently introduced UUIDs for disks etc have anything to do with this.

Many thanks.

---

### Post by hda on 2006-09-04
Hi!

Had the same problem when I found this post. Fortunately I found out what happened. After cloning the VMware virtual machine the network interface got renamed. Don't know why.

With ```
ifconfig -a
```I was able to see the new name of the interface. It was eth1 instead of eth0 (which appeared in dmesg). After changing the interface in /etc/network/interfaces everything was fine again.

hth

---

### Post by newlinux on 2006-09-04
I've had problems with the network interface mapping changing from login to login... (that's why I thought the problem might be the mapping). I ended up setting them in /etc/iftab using the MAC addresses obtained from ifconfig. Not sure how much different this is on a server install.

Just curious--
What's the difference between setting these in /etc/iftab and /etc/network/interfaces?

---

### Post by cat5 on 2006-09-05
editing the /etc/iftab on all cloned machines will most likely fix the issue - not all machines will have this mac, so in essence, eth0 is reserved for this MAC address, and eth1 will be the correct interface.

Remove the line, reboot, and see if it comes up.
I bet it does.

- Cat5

---

### Post by scmerisina on 2006-09-05
The "eth0 not found" problem after cloning a lab full of PCs is solved.  Indeed it has to do with the contents of /etc/iftab.  

On the "Golden Client" source machine the file /etc/iftab was generated by some setup script to name a specific NIC with a specific MAC address as eth0.  The other machines in the lab have same brand NICs but of course different MAC addresses as they are supposed to be GUID.  I should have checked this file.  So, udev and others would name the device as eth1 etc. and ifconfig, dhclient, ... fail even though dmesg shows that the driver loaded fine.  You can see the actual names of net devices in /proc/net/dev.

I changed the /etc/iftab to name the NIC as eth0 based on driver name rather than MAC.

Thanks to all.

---

### Post by blackeyeddog on 2007-07-09
I had the same problem and by reading all the thread I could find  another solution option.  I would like to share it, may it be helpful to other people, like your posts were to me. 

THE SITUATION
- Ubuntu Feisty (upgraded from Edgy some 3 weeks before) with VMWare running a Windows 98 machine without problem.
- made a Norton Ghost into a better hardware , with different NIC .
- VMware machine went "networkless", claiming on startup that "eth0 is down" . All the other applications kept on running fine.
- new environment had only eth1 . Forcefully trying to bring eth1 down and eth0 up , as suggested in this thread , was not successful.

THE SOLUTION
- checked eth1 MAC address with ifconfig
- checked /etc/iftab , had a single line for eth0 with old MAC address
- edited /etc/iftab , replaced etho MAC address with the new one
- reboot (just for sake, maybe "networking restart" would do the job) . VMWare OK !

As said above , /etc/iftab seems to define persistent eth's, possibly forcing modprobe to assign new eth numbers to different MAC addresses.

Thanks, folks.

---

### Post by reukiodo on 2007-08-15
> 
THE SOLUTION
- checked eth1 MAC address with ifconfig
- checked /etc/iftab , had a single line for eth0 with old MAC address
- edited /etc/iftab , replaced etho MAC address with the new one
- reboot (just for sake, maybe "networking restart" would do the job) . VMWare OK !


Is there a more permanent solution?  I would like to know how to configure modprobe to assign ethX to devices in the order found at boot without caching ethX names to MAC relations.  Is this possible?  Would it require a kernel modification?

Manually setting each iftab from an image for identical machines is APITA for something that is supposed to be automated.

---

### Post by reukiodo on 2007-08-16
After a little research, it seems to be a udev problem, specifically in:
/etc/udev/persistent-net-generator.rules
/etc/udev/rules.d/z25_persistent-net.rules

I found out that I needed to add ```
GOTO="persistent_net_generator_end"
``` to the beginning of /etc/udev/persistent-net-generator.rules and then remove all of the lines from /etc/udev/rules.d/z25_persistent-net.rules so the interface would always come up as eth0 regardless of MAC address.

Let me know if this works for you guys.  Finally this ghost image works on all the computers without modification.

---

### Post by phedre on 2007-09-05
> **reukiodo said:**
> After a little research, it seems to be a udev problem, specifically in:
/etc/udev/persistent-net-generator.rules
/etc/udev/rules.d/z25_persistent-net.rules
....
Let me know if this works for you guys.  Finally this ghost image works on all the computers without modification.

This fix worked for me, though I'm using debian sarge and not Ubuntu. Thanks!

---

### Post by adriano.cunha on 2008-03-06
Since linking MAC address and device name is a good feature, you should  remove the /etc/udev/rules.d/70-persistent-net.rules before you start cloning your TEMPLATE machine.

---

