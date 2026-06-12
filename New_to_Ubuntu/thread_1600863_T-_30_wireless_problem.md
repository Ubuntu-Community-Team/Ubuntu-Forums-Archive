---
title: "T- 30 wireless problem"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by yumyumsdad on 2010-10-19
Hi,

Just installed 10.10 on my IBM T-30 laptop yesterday and most things seem to be working except for the wireless connection. It connects fine on the wired connection. The OS recognizes the wireless chip but that seems to be all. Other than that, I'm having great fun looking around at the other stuff. 10.10 runs much faster than WinXP on this laptop which is one reason that I'm hoping to transition to Ubuntu. 

IBM 2366QU5
Intel P4-M CPU 2.40 GHz
512MB DDR Memory
56GB ATA HD
Video Adapter: ATI Mobility Radeon 7500
Network Adapter: Intel PRO/100 VE (Ethernet 100Mbps)
Wireless Adapter: High Rate Wireless LAN Mini-PCI Adapter with Modem II
Prism 2.5 Wavelan chipset  wifi0
SoundMAX Digital Audio
Power Scheme: Always On
192.168.1.1
255.255.255.0

Although I'm a true newbie, I have been around PCs for 30 years, so using the command line doesn't phase me - it is actually one of the attractions for me.

Any suggestions?

---

### Post by Hippytaff on 2010-10-19
you can do a number of things to try and diagnose the problem with command line

```

lspci

```to list the pci stuff and their chipsets to find the driver name (if you don't already know it.
```

iwconfig

```like ipconfig on ms but for wireless
```

lshw -C network

```shows network stuff

if you copy and paste the output here people will have a look and help you try to work it out. Also it might be worth checking to see if wireless is enabled in system > Preferences > network connections first :-)

forgot to mention, might be worth having a browse around the forums just incase someone has already worked out how to fix the same problem :-)

---

### Post by yumyumsdad on 2010-10-19
So I got this

wasp1957@wasp1957:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
wasp1957@wasp1957:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:6  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:834   Missed beacon:0

wasp1957@wasp1957:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:3c:09:ae:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:f8000000-f8000fff
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:0d:60:2c:f5:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.111 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:d0200000-d0200fff ioport:8000(size=64)
wasp1957@wasp1957:~$

---

### Post by Hippytaff on 2010-10-19
you can check to see if you module/driver is loaded with grep

```

grep -E "module/drivername" /proc/modules


```which I think might be prism2_pci (the linux driver)

if not you can get it here [http://wiki.debian.org/linux-wlan-ng](http://wiki.debian.org/linux-wlan-ng)

---

### Post by yumyumsdad on 2010-10-19
Sorry, I don't understand. What do I put in the expression "module/drivername"

---

### Post by Hippytaff on 2010-10-19
> **yumyumsdad said:**
> Sorry, I don't understand. What do I put in the expression "module/drivername"

Sorry replace 'module/drivername' with "prism2_pci" including the quotations

If its there it'll show up in the terminal, if not you might need to install it, but check to see if its there and if it is it'll be something else causing the problem :-)

---

### Post by yumyumsdad on 2010-10-19
I got this:

 grep -E "prism2_pci /proc/modules
binfmt_misc 6599 1 - Live 0xe07d2000
snd_intel8x0 25632 2 - Live 0xe09bf000
radeon 825934 3 - Live 0xe0c15000
snd_ac97_codec 99227 1 snd_intel8x0, Live 0xe0a54000
ac97_bus 1014 1 snd_ac97_codec, Live 0xe07d5000
snd_pcm 71475 2 snd_intel8x0,snd_ac97_codec, Live 0xe095f000
joydev 8735 0 - Live 0xe0843000
thinkpad_acpi 67659 0 - Live 0xe087f000
snd_seq_midi 4588 0 - Live 0xe07b4000
ttm 56633 1 radeon, Live 0xe0a17000
snd_rawmidi 17783 1 snd_seq_midi, Live 0xe09cc000
pcmcia 35973 0 - Live 0xe0898000
drm_kms_helper 30200 1 radeon, Live 0xe0935000
snd_seq_midi_event 6047 1 snd_seq_midi, Live 0xe0847000
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event, Live 0xe0864000
snd_timer 19067 2 snd_pcm,snd_seq, Live 0xe083c000
hostap_pci 44661 2 - Live 0xe08a2000
nsc_ircc 18252 0 - Live 0xe07a1000
drm 168054 5 radeon,ttm,drm_kms_helper, Live 0xe0a9a000
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xe0900000
ppdev 5556 0 - Live 0xe0872000
irda 178938 1 nsc_ircc, Live 0xe0988000
hostap 100441 1 hostap_pci, Live 0xe0908000
yenta_socket 21518 0 - Live 0xe07f1000
pcmcia_rsrc 10566 1 yenta_socket, Live 0xe0789000
snd 49006 12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xe0aeb000
psmouse 59033 0 - Live 0xe0924000
led_class 2633 1 thinkpad_acpi, Live 0xe078d000
intel_agp 26360 1 - Live 0xe0b10000
video 18712 0 - Live 0xe09e4000
parport_pc 26058 1 - Live 0xe08f2000
i2c_algo_bit 5168 1 radeon, Live 0xe09bb000
lib80211 5058 2 hostap_pci,hostap, Live 0xe0a2c000
pcmcia_core 14657 3 pcmcia,yenta_socket,pcmcia_rsrc, Live 0xe09f9000
output 1883 1 video, Live 0xe09d3000
nvram 6342 1 thinkpad_acpi, Live 0xe09c8000
crc_ccitt 1351 1 irda, Live 0xe0940000
serio_raw 4022 0 - Live 0xe0905000
shpchp 29886 0 - Live 0xe0875000
agpgart 32011 3 ttm,drm,intel_agp, Live 0xe08cf000
soundcore 880 1 snd, Live 0xe08ba000
snd_page_alloc 7120 2 snd_intel8x0,snd_pcm, Live 0xe08b0000
lp 7342 0 - Live 0xe0860000
parport 31492 3 ppdev,parport_pc,lp, Live 0xe084a000
e100 30356 0 - Live 0xe07de000
floppy 54311 0 - Live 0xe07b8000
mii 4425 1 e100, Live 0xe07c8000
wasp1957@wasp1957:~$

---

### Post by Hippytaff on 2010-10-19
Did you forget a quotation

> 
grep -E "prism2_pci /proc/modules
grep -E "prism2_pci" /proc/modules

will look down the list in the mean time :-)

Can't see it, might need to install it

[http://wiki.debian.org/linux-wlan-ng](http://wiki.debian.org/linux-wlan-ng)

---

### Post by yumyumsdad on 2010-10-19
Whoops. I ran the corrected expression but nothing shows up

---

### Post by Hippytaff on 2010-10-19
might need to install it - can get it here... [http://wiki.debian.org/linux-wlan-ng](http://wiki.debian.org/linux-wlan-ng)

---

### Post by sandyd on 2010-10-19
> **yumyumsdad said:**
> I got this:

 grep -E "prism2_pci /proc/modules
binfmt_misc 6599 1 - Live 0xe07d2000
snd_intel8x0 25632 2 - Live 0xe09bf000
radeon 825934 3 - Live 0xe0c15000
snd_ac97_codec 99227 1 snd_intel8x0, Live 0xe0a54000
ac97_bus 1014 1 snd_ac97_codec, Live 0xe07d5000
snd_pcm 71475 2 snd_intel8x0,snd_ac97_codec, Live 0xe095f000
joydev 8735 0 - Live 0xe0843000
thinkpad_acpi 67659 0 - Live 0xe087f000
snd_seq_midi 4588 0 - Live 0xe07b4000
ttm 56633 1 radeon, Live 0xe0a17000
snd_rawmidi 17783 1 snd_seq_midi, Live 0xe09cc000
pcmcia 35973 0 - Live 0xe0898000
drm_kms_helper 30200 1 radeon, Live 0xe0935000
snd_seq_midi_event 6047 1 snd_seq_midi, Live 0xe0847000
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event, Live 0xe0864000
snd_timer 19067 2 snd_pcm,snd_seq, Live 0xe083c000
hostap_pci 44661 2 - Live 0xe08a2000
nsc_ircc 18252 0 - Live 0xe07a1000
drm 168054 5 radeon,ttm,drm_kms_helper, Live 0xe0a9a000
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xe0900000
ppdev 5556 0 - Live 0xe0872000
irda 178938 1 nsc_ircc, Live 0xe0988000
hostap 100441 1 hostap_pci, Live 0xe0908000
yenta_socket 21518 0 - Live 0xe07f1000
pcmcia_rsrc 10566 1 yenta_socket, Live 0xe0789000
snd 49006 12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xe0aeb000
psmouse 59033 0 - Live 0xe0924000
led_class 2633 1 thinkpad_acpi, Live 0xe078d000
intel_agp 26360 1 - Live 0xe0b10000
video 18712 0 - Live 0xe09e4000
parport_pc 26058 1 - Live 0xe08f2000
i2c_algo_bit 5168 1 radeon, Live 0xe09bb000
lib80211 5058 2 hostap_pci,hostap, Live 0xe0a2c000
pcmcia_core 14657 3 pcmcia,yenta_socket,pcmcia_rsrc, Live 0xe09f9000
output 1883 1 video, Live 0xe09d3000
nvram 6342 1 thinkpad_acpi, Live 0xe09c8000
crc_ccitt 1351 1 irda, Live 0xe0940000
serio_raw 4022 0 - Live 0xe0905000
shpchp 29886 0 - Live 0xe0875000
agpgart 32011 3 ttm,drm,intel_agp, Live 0xe08cf000
soundcore 880 1 snd, Live 0xe08ba000
snd_page_alloc 7120 2 snd_intel8x0,snd_pcm, Live 0xe08b0000
lp 7342 0 - Live 0xe0860000
parport 31492 3 ppdev,parport_pc,lp, Live 0xe084a000
e100 30356 0 - Live 0xe07de000
floppy 54311 0 - Live 0xe07b8000
mii 4425 1 e100, Live 0xe07c8000
wasp1957@wasp1957:~$
It looks fine to me, the prism driver is built into the kernel. hostap_pci is loaded. According to the bug, its supposed to work in Maverick, so if you havent got maverick installed, don't bother. hostap_pci for your card is screwed up on Karmic

try installing linux-backports-modules, as mentioned -> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432636/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432636/comments/12)

---

### Post by yumyumsdad on 2010-10-19
OK. So I wound up here [http://packages.debian.org/lenny/linux-wlan-ng-source](http://packages.debian.org/lenny/linux-wlan-ng-source) but I don't know what do do next. Sorry.

---

### Post by yumyumsdad on 2010-10-19
> **sandyd said:**
> It looks fine to me, the prism driver is built into the kernel. hostap_pci is loaded. According to the bug, its supposed to work in Maverick, so if you havent got maverick installed, don't bother. hostap_pci for your card is screwed up on Karmic

try installing linux-backports-modules, as mentioned -> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432636/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432636/comments/12)
I have Maverick. How do I install that package

---

### Post by Hippytaff on 2010-10-19
What I'm suggesting is to download a different driver, because hostap_pci doesn't seem to be working, but I might be wrong so you might want to wait until someone else offers something.

it might be a potch, installing the dependencies then compiling the driver if that's not the issue...

just out of curiosity what does

```

rfkill list

```return

---

### Post by yumyumsdad on 2010-10-19
nothing

---

### Post by yumyumsdad on 2010-10-19
Thanks very much for all the assistance so far.

It is obvious that Ubuntu will do anything that I need to do with this old laptop.  Right now I have a dual boot set up and am wanting to have my laptop as a pure linux machine.  When I got to reinstall, do I start all over again from scratch or do any changes I made in the dual boot system I have be remembered?  I assume I'll lose everything, is that correct? Because if that is true, then I may as well top trying to solve the wireless problem until I reinstall.

Also looking at my computer's spec, do you think that I am better off with xubuntu? 

Comments?

---

### Post by Hippytaff on 2010-10-19
you can doenload the .deb package here [http://packages.debian.org/lenny/all/linux-wlan-ng-source/download](http://packages.debian.org/lenny/all/linux-wlan-ng-source/download)

I've never compiled a driver from source before...so I'm just as in the dark as you at this point...I'll see if I can find any decent tutorials :-)

---

### Post by Hippytaff on 2010-10-19
Right...seems far easier than I thought using synaptic manager...go to system > Administration > synaptic package manager

in the search bit put linux-wlan-ng. You should see it in the window below. click on it and see if it is the one for prism2 (in the description bit). If it is you can download and install it by checking the box to the left of it. It will ask you to mark for installation. click that and then click apply...hope it works :-)

You might have to reboot?

---

### Post by sandyd on 2010-10-19
> **yumyumsdad said:**
> I have Maverick. How do I install that package
```

sudo apt-get install linux-backports-modules
```

---

### Post by Hippytaff on 2010-10-19
> **sandyd said:**
> ```

sudo apt-get install linux-backports-modules
```

Sorry...thought op was asking me :-)

---

### Post by yumyumsdad on 2010-10-20
> **sandyd said:**
> ```

sudo apt-get install linux-backports-modules
```


I got

wasp1957@wasp1957:~$ sudo apt-get install linux-backports-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules
wasp1957@wasp1957:~$

---

### Post by Hippytaff on 2010-10-20
> **Hippytaff said:**
> Right...seems far easier than I thought using synaptic manager...go to system > Administration > synaptic package manager

in the search bit put linux-wlan-ng. You should see it in the window below. click on it and see if it is the one for prism2 (in the description bit). If it is you can download and install it by checking the box to the left of it. It will ask you to mark for installation. click that and then click apply...hope it works :-)

You might have to reboot?

give this a bash.

---

### Post by yumyumsdad on 2010-10-20
> **Hippytaff said:**
> give this a bash.

I got and installed the package with no problems thewn rebooted. Still nothing.  Am I missing a step?

Thanks

---

### Post by Hippytaff on 2010-10-20
So you've done what is in the screen shot, then selected apply...restarted and nothing?

---

### Post by yumyumsdad on 2010-10-20
> **Hippytaff said:**
> So you've done what is in the screen shot, then selected apply...restarted and nothing?

Exactly. And my wireless is totally unprotected until I figure this out

---

