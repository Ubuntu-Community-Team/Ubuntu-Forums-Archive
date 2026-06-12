---
title: "wireless issues (&quot;device not managed&quot;)"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Nemo103 on 2011-07-30
In the networking icon on the panel it says under wireless networks "device not managed". It works fine when I boot in windows.
It's a Broadcom Corporation BCM43225 on an Acer Aspire 5741, and I'm using 11.04.


iwconfig gives:
```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

I've tried all sorts. I'm considering just starting the entire OS over...
Please help!

---

### Post by wildmanne39 on 2011-07-30
Hi, run these commands please
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
rfkill list all
```
and post the results here.
Thank you

---

### Post by Nemo103 on 2011-07-30
Yes (:
sudo lshw -C network:```
*-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 70:5a:b6:c9:67:a5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=192.168.11.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:b3400000-b340ffff
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:8b:b4:a3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-10-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2400000-b2403fff
```

lspci -nn | grep 0280:```
.02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

```

and rfkill list all:```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by wildmanne39 on 2011-07-30
Hi, run this command
```
sudo apt-get install b43-fwcutter
```
then after it is finished unplug your wire connection and restart your computer and see if it works.
Thank you

---

### Post by Nemo103 on 2011-07-30
Hi,
it said something about already being installed. On restarting, the wireless still said unmanaged, and the result of iwconfig was the same as before.
Thanks

---

### Post by wildmanne39 on 2011-07-30
Hi, click on the zip file it is a script that fixes wireless issue created by lkjoel.

Copy it to your desktop then do this.
```
cd ~/Desktop
chmod +x wirelessGUI.sh
./wirelessGUI.sh &
```
then just answer the questions and it will most likely fix your problem.
You will need to enter you password every time it asks for it.

This should work unless there is a drivers issue. Please let me know and we will go from there.
Thank you

---

### Post by Nemo103 on 2011-07-30
Hi,
that hasn't done anything, sorry

---

### Post by wildmanne39 on 2011-07-30
Hi, open synaptic make it where it shows everything that is installed for your driver, then take a screenshot and post it here please.

Did you try ndiswrapper or nay ohter drivers?
Thank you

---

### Post by Nemo103 on 2011-07-30
Sorry, I don't know how to show just what's installed for the driver. Here's what came up for "bcm" and "driver" (only 2), and "driver" and "wireless"

I remember trying ndiswrapper at some point, as well as quite a few others. The broadcom STA is there but not active now. I've rather lost track...

---

### Post by wildmanne39 on 2011-07-30
Hi, uninstall everything that has to do with ndiswrapper by right clicking on them and choose remove completely. 

Then disconnect your wired connection and restart your computer and see if that makes it work if not we will be one step closer.
Thank you

---

### Post by Nemo103 on 2011-07-30
Nothing.
But you sound like you have a plan

---

### Post by wildmanne39 on 2011-07-30
Hi, that narrows things down and I am going to give some commands that will narrow it down further.
```
lsmod | grep brcm80211

```
```
dmesg | grep brcm80211
```
```
dmesg | grep firmware
```
```
sudo iwlist scan
```
```
modinfo brcm80211

```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Nemo103 on 2011-07-30
lsmod | grep brcm80211
```
brcm80211             682265  0 
mac80211              257001  1 brcm80211
cfg80211              156212  2 brcm80211,mac80211

```

dmesg | grep brcm80211
```
[   21.516151] brcm80211 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.516161] brcm80211 0000:02:00.0: setting latency timer to 64

```

dmesg | grep firmware
-nothing-


sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:01:59:BF:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"BUFFALO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031ef664b188
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000742554646414C4F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD06001018020013

```

modinfo brcm80211
```
filename:       /lib/modules/2.6.38-10-generic-pae/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     370CDCBC47C65D9E86B1F33
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
vermagic:       2.6.38-10-generic-pae SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int

```

thanks

---

### Post by wildmanne39 on 2011-07-30
Hi, run these commands please
```
cat /etc/network/interfaces
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
lsmod
```
```
dmesg | grep wlan0
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

We are close so don't give up.
Thank you

---

### Post by Nemo103 on 2011-07-30
cat /etc/network/interfaces```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

```


cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

lsmod
```
Module                  Size  Used by
snd_hrtimer            12680  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  450969  8 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13666  0 
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184133  4 i915,drm_kms_helper
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                59039  0 
intel_ips              17769  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
arc4                   12473  2 
brcm80211             682265  0 
mac80211              257001  1 brcm80211
cfg80211              156212  2 brcm80211,mac80211
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
tg3                   131476  0 
```


dmesg | grep wlan0
```
[   21.656304] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

eeeeep

---

### Post by wildmanne39 on 2011-07-30
Hi, ok we found one problem.
run this command
```
gksu gedit
```
then at the top of the window click on open then browse to the filesystem etc folder and then the network folder and open the interfaces file, then delete [B]auto wlan0
iface wlan0 inet dhcp[/B]then save and close then unplug wired connection and restart ubuntu.
Thank you

---

### Post by Nemo103 on 2011-07-31
Hi,
I've done that, but now it won't boot. In normal mode it just seems to hang where it says Ubuntu with five dots underneath. In recovery mode I think it shows the kernel message buffer as it happens, but it just keeps going.
In each case it carries on like that until it overheats and cuts the power (as it's been prone to do since the fan stopped working a few days ago...)
Thanks

---

### Post by zero2xiii on 2011-07-31
> Hi,
I've done that, but now it won't boot. In normal mode it just seems to hang where it says Ubuntu with five dots underneath. In recovery mode I think it shows the kernel message buffer as it happens, but it just keeps going.
In each case it carries on like that until it overheats and cuts the power (as it's been prone to do since the fan stopped working a few days ago...)
Thanks

Deleting those lines from the file would not have caused this issue, haha I STRONGLY suggest to first get your fan fixed, you are corupting data by the hard resets done by the BIOS due to overheating...

---

### Post by wildmanne39 on 2011-07-31
Hi, I am sorry to hear that, changing the network file would not have caused that,unless you changed some other file while you had gedit open, but I do not think that is the case.

I am surprised your computer even turned on without the fan working,I had one that the fan went out on and it did not even turn on until I fixed it to prevent causing damage to the computer.

If you had an update last night during what we were doing you can try this link to get you into ubuntu, it is for setting nomodeset parameters.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If you have been hard resetting then you most likely have hard drive with bad sectors and file corruption.

---

### Post by obryanjf on 2011-11-12
Success, no expert here, but removed, killed and reinstalled all kinds of stuff.  I have a HP mini with a Broadcom 4311.  I have the STA driver active now and then editied out from /etc/network file:
 
delete auto lo, iface lo inet loopback, iface eth1 inet dhcp, wireless-essid *****, wireless-mode managed.
 
left only with 
auto lo
 
I turned off the wireless and the ethernet still works, and the wireless comes back on.  thanks

---

### Post by sadaruwan12 on 2011-11-12
It's not due to deleting the lines from network file it's some thing else.

It might be a case of corrupted file due to hard reset I had to face this once and had redo the full system.

Best thing to is fix your fan and reinstall your system. If you want to get  a backup you can use the live CD to do that.

---

### Post by macsj200 on 2012-01-16
Assuming you're using nm-applet, try editing /etc/NetworkManager/NetworkManager.conf from 

```

[ifupdown]
managed=false

```

to

```

[ifupdown]
managed=true

```

Worked for me ;)

---

