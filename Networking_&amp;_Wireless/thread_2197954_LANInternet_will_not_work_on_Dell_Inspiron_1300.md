---
title: "LAN/Internet will not work on Dell Inspiron 1300"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by floko2 on 2014-01-06
Hi,
I am looking for help to get internet access from a freshly installed Ubuntu.
Having read a lot of threads about this around here, I tried to provide as much information as possible below (so pls. accept my excuse for this lengthy post)

I installed Ubuntu (12.04.3 LTS Release i386) on a Dell Inspiron 1300 Laptop from a USB stick.
During installation, Ubuntu obviously had internet access, as language packages have been downloaded.
However, since installation is complete and the system boots from HD, I have problems connecting to the net.
An ethernet cable directly connects the DSL modem to the laptop.
(This works perfectly with every other computer in the house.)  

 
This is how the network is configured: (ifconfig -a)
lo        Link encap:Local Loopback
          inet Addr:127.0.0.1  Mask:255.0.0.0
          inet6-Addr: ::1/128 Scope:Machine
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX-Bytes:13344 (13.3 KB)  TX-Bytes:13344 (13.3 KB)

Here is some information about the hardware (lspci -nnk | grep -i net -A2)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel modules: b44
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel modules: ssb
 

Based on the information I found in similar threads, I also tried the following (without success):

edit "/var/lib/NetworkManager/NetworkManager.state" and change it to "NetworkingEnabled=true"
(this file did not even exist, so I created it with this content)
I restarted the service afterwards; no connection.

I tried a different LAN port in the DSL modem, no difference.

I tried both
ping -c1 [www.google.de]("http://www.google.de") 
and 
ping -c1 173.194.113.151 (some Google IP)
Both did not work, so it's not an issue with the nameservers.

I should add that after one of several restarts the ethernet connection worked one single time (!),
without having changed any setting (!) before that specific restart.
But afterwards it did not work anymore.
I also tried it at my father's home (for whom the laptop is intended actually), who has a DSL connection 
from a completely different local provider, a different DSL modem and a different ethernet cable.
So I guess all of these cannot be held responsible for the problem (provider, modem, cable).

Thanks for any helpful idea!
floko

---

### Post by floko2 on 2014-01-08
Hi,
I just installed Ubuntu 12.04.3 LTS Release i386 on my father's old laptop, a Dell Inspiron 1300.
During installation from a USB stick, wired connection worked fine (some language packages have been downloaded obviously).

But following installation, I had internet access only once after a couple of restarts.
I then thought everything was fine (setup complete or something like this), and brought the laptop back to my father's home.
Then again we had no connection via ethernet cable.

So I took it back to me (because there I had connection at least once before), but ever since it did not work anymore.

Any idea would could be wrong here?
Thanks!

---

### Post by mörgæs on 2014-01-08
Threads merged.

---

### Post by floko2 on 2014-01-08
Based on similar threads here, I tried to get some more data - pls. see below...
I just hope someone is able to understand what this means and give me a hint what to try next.
Thanks!

cat /etc/network/interfaces
auto lo
iface lo 
inet loopback

----------

cat /etc/network/resolv.conf
file or folder not found

-----------------

lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48053  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
snd_hda_codec_idt      64649  1 
snd_hda_intel          38819  3 
snd_hda_codec         118613  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17329  0 
i915                  550346  3 
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            17209  0 
psmouse                82769  0 
drm_kms_helper         47749  1 i915
snd_timer              28931  2 snd_pcm,snd_seq
drm                   233935  4 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13031  0 
gpio_ich               13278  0 
dcdbas                 14065  1 dell_laptop
microcode              18433  0 
lpc_ich                17048  0 
i2c_algo_bit           13316  1 i915
snd                    57014  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
mac_hid                13077  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp

---

### Post by Iowan on 2014-01-08
*/etc/resolv.conf* - not */etc/network/resolv.conf*
> **floko2 said:**
> An ethernet cable directly connects the DSL modem to the laptop.
(This works perfectly with every other computer in the house.) 
There is no router in there? Frequently, a modem will "lock onto" a MAC address and must be reset when connected to a different MAC. A router provides a consistent (non-changing) MAC address. Is there a switch/hub attached? Either a router, switch, or hub would be needed to connect more than one computer at a time.

I'm curious why the interface (eth0?) doesn't appear in **ifconfig -a**

If it starts looking like a driver problem, I'm outta my league. Dunno if the B44 is right, or not...
From my 12.04 machine, */var/lib/NetworkManager/NetworkManager.state*:
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by floko2 on 2014-01-09
Thanks, Iowan.
In both cases (at my father's home and mine), it's a modem with integrated router. Both have multiple ports for LAN cables, so that is probably a hub then...?

*The file you mentioned (/var/lib/NetworkManager/NetworkManager.state*) did not exist on my system after installation.
     I created it (having read about this here) and filled it with "NetworkingEnabled=true".
When I am back at home this evening I will also add the two addtl. lines you suggested.
But I wonder if Ubuntu will load/execute what's in there even if it did not exist before?

Yesterday I also tried running "sudo dhclient eth0" to start the network manager manually, as I read somewhere.
This resulted in: "cannot find device eth0"
Does this help finding the cause for the problem in some way?
Thanks again!

---

### Post by mark65ak on 2014-01-09
You are not going to be able to ping anything because your network adapter is not up or even seen by the system.   the ifconfig results you posted are only showing a loopback connection labled "lo" and that seems to be fine.   the results you are needing should be similat but labled something like eth0  with the Link showing HWaddr and the mac address rather than loopback

---

### Post by mark65ak on 2014-01-09
Also when you say you are connecting straight to a modem, is this a modem with a build in router?  At both location?
Are you trying to connect via DHCP?  PPOE?  
Does this connection require authenticating each time or is it always on and ready?
Have you considered its the router and not the laptop?  Have you reset the router/modem?  And then tried?

---

### Post by floko2 on 2014-01-09
Thanks mark65ak for your thoughts!
Yes, both modems (although from different brands) have built in routers.
Honestly, I don't know which way I'm trying to connect. I suppose it's DHCP...
I don't think it requires authentication because I can plug the cable to a different laptop and it works without problems or further set up.
It's not the modem because both modems work fine with different laptops (and worked even fine with this very laptop when there still was Windows running on it).

---

### Post by mark65ak on 2014-01-09
Sorry for the redundant questions I see now you aready answered.

In regards to /var/lib/NetworkManager/NetworkManager.state the machine I am on now is like a 7 year old Gateway laptop that came with Vista anf that file does not exist and I rarely if ever have had network issues with this machine, though it has plenty in other ways.

I also have dell insiration mini and it does have it.  Very much like Iowans with the addtion of a 4th key pair WimaxEnable=true

I have no clue what this file is for but it appears it's not needed for networking.

In regards to /etc/network/interfaces mine is on 2 lines.  Not sure it that makes a difference
```
auto lo
iface lo inet loopback
```

---

### Post by floko2 on 2014-01-09
Good to know it should also works without the file NetworkManager.state.

I have exactly the same lines in /etc/network/interfaces as you have, so that should be no problem either.
But I will of course try the two addtl. lines from Iowan tonight, just to be sure.

---

### Post by floko2 on 2014-01-10
As Iowan pointed out, eth0 is missing in ifconfig.
I felt that this might be the root of the problem, so I tried something new: 
(as found here [http://www.serenux.com/2009/11/howto-fix-a-missing-eth0-adapter-after-moving-ubuntu-server-from-one-box-to-another/]("https://3c.gmx.net/mail/client/dereferrer?redirectUrl=http%3A%2F%2Fwww.serenux.com%2F2009%2F11%2Fhowto-fix-a-missing-eth0-adapter-after-moving-ubuntu-server-from-one-box-to-another%2F"))

I commented out all lines starting with "SUBSYSTEM" in /etc/udev/rules.d/70-persistent-net.rules
(I had 3 entries in there including eth0, eth1 and eth2) and restarted the system.

Still no conncetion. 
As I opened the file again, there was no new rule added automatically as described in above link.
So I removed the comment marks again to reset the file to its original state.

I have no clue what to do next...
Any idea how to get eth0 appearing in ifconfig? :confused:




[COLOR=#000080]
[/COLOR]

---

### Post by floko2 on 2014-01-10
Did I mention that a wired connection is instantly available as soon as I boot from USB stick?
(As it was during installation)
I can't believe it's not possible to get the same setting for the installed system... :-(

---

### Post by chili555 on 2014-01-10
Although your ethernet is supposed to work with the driver *b44*, it isn't loaded according to your lsmod. Does the ethernet spring to life if you do:```
sudo modprobe b44
```If it does, the driver is probably blacklisted somewhere. The most likely candidate is /etc/modprobe.d/blacklist-bcm43.conf. You can get* b44* to load by removing the blacklist:```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```This file is created when you install bcmwl-kernel-source; if it isn't purged, the file remains.> 02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
[COLOR="#FF0000"]Kernel modules: ssb[/COLOR]It looks like the wireless isn't currently in use. If you need it, we'll need more surgery. For now, I'm confident the ethernet will work now.

---

### Post by floko2 on 2014-01-10
You are confident the ethernet will work? With good reason! :-D
That's it - everything runs perfectly now. 
(I am not going to ask why on earth someone would blacklist this driver...)

Thank you so much!

I cannot express how thankful I am!!!

---

### Post by chili555 on 2014-01-10
Happy to help! Glad it's working.

I don't know why this happens, but sometimes a thread that's getting a bit long cries out to me; "Read me! Read me!"

---

