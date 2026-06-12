---
title: "Wired connection not showing"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by jcengel on 2013-12-03
Firstly, I have been using ubuntu for a year and absolutely love it. I haven't had any problems that I couldn't fix until now. I recently switched my modem router combo from an SMC to a Motorola sbg6580. after setting up the new router/modem, My wired connection did not show in ubuntu network manager and i could not connect through wired, but wireless connections did show and I was able to connect wirelessly (my wireless card on my desktop is junk and pretty unusable). I have win7 on another hard drive that I recently set up and booted from and connected no problem to the wired connection. This might also have something to do with it.

In an attempt to fix it from google web searches and by entering commands into the terminal I believe I may have screwed the pooch and deleted the network manager. I'd love to post up more info about what's going on but I really am not sure what commands I would need to use to bring up a troubleshooting tree.  This is some of the stuff I have punched blindly into the terminal hoping for a fix.

[http://askubuntu.com/questions/161482/wired-connection-not-working-ubuntu-12-04](http://askubuntu.com/questions/161482/wired-connection-not-working-ubuntu-12-04)

[http://askubuntu.com/questions/230698/how-to-restart-the-networking-service](http://askubuntu.com/questions/230698/how-to-restart-the-networking-service)

please please tell me i don't need to back up and reinstall ubuntu all together.

---

### Post by PaulBx on 2013-12-03
Seems like you could re-install the network manager if you actually messed it up, but it's hard to see how you could do that. Also, there may be more than one kind of network manager. The one in lubuntu is simple and functional.

Is your eth0 driver correct?

Usually ethernet is the easy one to get working. Maybe there is some setup needed in the new router, to make it friendlier to Ubuntu.

---

### Post by Iowan on 2013-12-03
Does wireless still work?
Is Network Manager icon still there (does it do anything)?
Check (and post, if possible) the contents of */etc/network/interfaces*.

---

### Post by jcengel on 2013-12-04
Network manager icon is not there anymore on the unity toolbar. Before I made it go bye bye the wireless would connect but with my junky wireless card it is pretty much unusable. In the etc/network/interfaces document this is what I have:



> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

i think this is one of the files I edited per the above links.

All of my drivers should be fine considering my wired connection worked before I switched my modem/router and connected an extra windows 7 hd.

---

### Post by Iowan on 2013-12-04
If that is actually what's in your */etc/network/interfaces*, it has a couple of typos - should look more like:
```
auto lo
iface inet loopback
auto eth0
iface eth0 inet dhcp
```Dunno if it's actually causing problems...

My Network Manager icon (12.04) is in the top right corner of the screen.

---

### Post by jcengel on 2013-12-04
[ATTACH=CONFIG]248347[/ATTACH]Also on startup it does this, it didn't do this before and ubuntu takes much longer than normal to boot up.

---

### Post by jcengel on 2013-12-04
Just changed the file and rebooting now, will update soon. thanks for your time.

Still shows the "waiting for network config at startup

:/

No luck. Network manager still isn't showing on the tool bar.

---

### Post by jcengel on 2013-12-07
I'm going to backup all my important stuff and upgrade to the newest version. That should fix it.

---

### Post by jcengel on 2013-12-07
I just backed everything up and was about to do a full re-install of 12.04 but before I did a ran the test drive just to see if my wired connection would connect.  It did not connect. I also tried it from lubuntu and the same results.  I also tried pinging my router from network tools "192.168.0.1" as per Motorola gateway url. I could not ping my router. I really wish I knew more about network stuff. I have some more info that I pulled from terminal and put on a usb stick. Anything would help at this point. I am really getting tired of win7 already.

```
 $[B] ifconfig
[/B]
eth0      Link encap:Ethernet  HWaddr 40:61:86:94:18:ba  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:41 Base address:0x4000 


eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:94:18:ba  

          inet addr:169.254.8.44  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:41 Base address:0x4000 


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:788 errors:0 dropped:0 overruns:0 frame:0

          TX packets:788 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:59936 (59.9 KB)  TX bytes:59936 (59.9 KB)



$[B] cat /etc/lsb-release; uname -a
[/B]
DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=12.04

DISTRIB_CODENAME=precise

DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

Linux Daddy-o 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 09:20:45 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

joshua@Daddy-o:~$ lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)

    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]

    Kernel driver in use: r8169

--

03:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)

    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]

    Kernel driver in use: wl

    Kernel modules: wl, ssb



$[B] lsusb
[/B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub

Bus 001 Device 003: ID 046d:0819 Logitech, Inc. Webcam C210

Bus 001 Device 004: ID 03f0:7511 Hewlett-Packard 

Bus 001 Device 005: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse

Bus 002 Device 003: ID 0781:5575 SanDisk Corp. 

Bus 002 Device 004: ID 0bc2:3001 Seagate RSS LLC 



[B]$ iwconfig
[/B]
lo        no wireless extensions.


eth2      IEEE 802.11abg  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          

eth0      no wireless extensions.




$[B] rfkill list all
[/B]
0: phy0: Wireless LAN

    Soft blocked: no

    Hard blocked: no

1: brcmwl-0: Wireless LAN

    Soft blocked: no

    Hard blocked: no

joshua@Daddy-o:~$ lsmod

Module                  Size  Used by

iwlwifi               401148  0 

mac80211              506862  1 iwlwifi

rfcomm                 47604  0 

parport_pc             32866  0 

ppdev                  17113  0 

bnep                   18281  2 

bluetooth             180113  10 rfcomm,bnep

binfmt_misc            17540  1 

lib80211_crypt_tkip    17390  0 

snd_hda_codec_realtek   224173  1 

serio_raw              13211  0 

snd_hda_intel          33719  3 

snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel

snd_usb_audio         122982  1 

snd_pcm                97275  3 snd_hda_intel,snd_hda_codec,snd_usb_audio

snd_hwdep              17764  2 snd_hda_codec,snd_usb_audio

snd_usbmidi_lib        29476  1 snd_usb_audio

snd_seq_midi           13324  0 

snd_seq_midi_event     14899  1 snd_seq_midi

snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event

nvidia              11308613  40 

wl                   3074895  0 

usblp                  18307  0 

usbhid                 47238  0 

snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi

uvcvideo               72627  0 

hid                    99636  1 usbhid

videodev               98259  1 uvcvideo

snd_timer              29990  2 snd_pcm,snd_seq

v4l2_compat_ioctl32    17128  1 videodev

mac_hid                13253  0 

cfg80211              205774  3 iwlwifi,mac80211,wl

lib80211               14381  2 lib80211_crypt_tkip,wl

snd_seq_device         14540  3 snd_seq_midi,snd_seq,snd_rawmidi

snd                    79041  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device

mei                    41616  0 

soundcore              15091  1 snd

snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

lp                     17799  0 

parport                46562  3 parport_pc,ppdev,lp

usb_storage            49198  2 

r8169                  62190  0 

```





Thanks for your time.

Josh

---

### Post by varunendra on 2013-12-07
I going to suggest this same *possible* solution a third or maybe fourth time in last few days, although so far no one has confirmed whether it worked or not.

Please try the proprietary driver for your card following this [post=12858051]post[/post], and let us know if it makes your Ethernet work again.

**PS:**
You should use 'Code' tags to post the outputs, not the 'Quote' tags that you have used above. It preserves the formatting of the output, makes the post cleaner, compact and more readable. Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by jcengel on 2013-12-07
Thanks for your time. My above post was edited for convenience. I downloaded the driver and ran it from terminal as suggested. It didn't complete and gave me an error.

---

### Post by jcengel on 2013-12-07
You guys are gonna laugh... my ethernet wasn't plugged into my router. I have a blue cable that goes to my computer and a spare blue cable that goes to nothing.  Guess which one I had plugged in? I still do have the problem of no network manager after I seemed to delete it but at least now my internet is working. What's a good terminal command to download network manager? Also, will I need to reverse what I did before with the driver?

---

### Post by varunendra on 2013-12-07
> **jcengel said:**
> ..I have a blue cable that goes to my computer and a spare blue cable that goes to nothing.  Guess which one I had plugged in?
:lolflag:

> I still do have the problem of no network manager after I seemed to delete it but at least now my internet is working. What's a good terminal command to download network manager? Also, will I need to reverse what I did before with the driver?
If the connection is working on each reboot, the driver, whichever it is, is fine and nothing needs to be reverted.

However, if you wish to use Network Manager to handle the connection, you will have to reset the /etc/network/interfaces file back to defaults. That is, it should only contain -
```
auto lo
iface lo inet loopback
```

To install/reinstall Network Manager (before resetting the interfaces file of course) -
```
sudo apt-get update
sudo apt-get install --reinstall network-manager-gnome
```
You may have to reboot or manually do -
Alt+F2 > nm-applet
to get the nm-applet icon in the systray if it doesn't automatically come up after reinstalling.

---

### Post by jcengel on 2013-12-08
Thanks so much for your help Varunendra. I have my network manager back, it is still not showing on systray but I am able to access it through the dash after reboot. I think we can mark this thread solved. I feel really stupid :D

edit: I added nm-applet to the startup applications preferences and it is back on the toolbar. I am happier than a pig in slop :)

---

