---
title: "wireless connection fails, Lucid Lynx 64-bit"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by _niai on 2011-03-01
Hello,
 
I am new to Linux and I know close to nothing about working with it, so I have no clue where the problem comes from.
 
Here it is: I had the 32-bit version of Lucid (on a Dell laptop) and just installed the 64-bit one.
Before the installation, using the live CD, I used cable connection to the internet and it worked, and I let the laptop connected during installation.
When the process was completed, an icon appeared and suggested I download and install Broadcom STA wireless driver, which I did.
(The same happened when installing the 32-bit version of Lucid and I had no problems with that one.)
Cable still works. I cannot log on to my wireless network though.
I see it in the drop down menu, but when I try to connect it just doesn't happen, the window for the password comes up again and again.
(I am certain the password is correct, I have it written and keep it with the router's documentation.)
 
I tried searching the forum and I found this suggestion:
[http://http://ubuntuforums.org/showthread.php?t=1617549](http://http://ubuntuforums.org/showthread.php?t=1617549)
I have no idea what the deal is with these files and whether or not it can be relevant to my problem, but I tried it anyway. Nothing changed after restart.
 
I also found this:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
Ok, this is going to be very very long...
 
> 
[FONT=Courier New][SIZE=2]~$ lspci[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ lsusb[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 008: ID 413c:8160 Dell Computer Corp. [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 006: ID 413c:8162 Dell Computer Corp. [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 005: ID 413c:8161 Dell Computer Corp. [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 003: ID 046d:c52f Logitech, Inc. [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 002: ID 8087:0020 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 001 Device 003: ID 0c45:641d Microdia [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 001 Device 002: ID 8087:0020 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ ifconfig[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]eth0 Link encap:Ethernet HWaddr f0:4d:a2:aa:66:37 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]UP BROADCAST MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]RX packets:12 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]TX packets:29 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]RX bytes:2304 (2.3 KB) TX bytes:4677 (4.6 KB)[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Interrupt:33 Base address:0x8000 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]eth1 Link encap:Ethernet HWaddr 1c:65:9d:79:b0:7e [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]inet6 addr: fe80::1e65:9dff:fe79:b07e/64 Scope:Link[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]RX packets:0 errors:0 dropped:0 overruns:0 frame:211029[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]TX packets:128 errors:8 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]RX bytes:0 (0.0 B) TX bytes:26228 (26.2 KB)[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Interrupt:17 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]lo Link encap:Local Loopback [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]RX packets:780 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]TX packets:780 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]collisions:0 txqueuelen:0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]RX bytes:58532 (58.5 KB) TX bytes:58532 (58.5 KB)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ iwconfig[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]lo no wireless extensions.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]eth0 no wireless extensions.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]eth1 IEEE 802.11 Access Point: Not-Associated [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Link Quality:5 Signal level:199 Noise level:169[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Rx invalid nwid:0 invalid crypt:0 invalid misc:0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]pan0 no wireless extensions.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ lsmod[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Module Size Used by[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nls_iso8859_1 4633 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nls_cp437 6351 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]vfat 10866 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]fat 55350 1 vfat[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]usb_storage 49961 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ipt_MASQUERADE 1863 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]xt_state 1490 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ipt_REJECT 2384 2 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]xt_tcpudp 2667 4 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]iptable_filter 2791 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_h323 5978 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_h323 55193 1 nf_nat_h323[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_pptp 2245 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_pptp 5566 1 nf_nat_pptp[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_proto_gre 4798 1 nf_conntrack_pptp[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_proto_gre 1719 1 nf_nat_pptp[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_tftp 1017 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_tftp 4001 1 nf_nat_tftp[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_sip 6169 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_sip 18894 1 nf_nat_sip[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_irc 1577 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_irc 4429 1 nf_nat_irc[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat_ftp 2513 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_ftp 7126 1 nf_nat_ftp[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]iptable_nat 5219 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_nat 19501 9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack_ipv4 12980 4 iptable_nat,nf_nat[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_conntrack 73966 18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]nf_defrag_ipv4 1481 1 nf_conntrack_ipv4[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ip_tables 18390 2 iptable_filter,iptable_nat[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]x_tables 22461 6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]binfmt_misc 7960 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]rfcomm 40393 4 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]sco 9649 2 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ppdev 6375 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]bridge 53216 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]stp 2171 1 bridge[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]bnep 11884 2 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]l2cap 34807 16 rfcomm,bnep[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_hda_codec_atihdmi 3023 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_hda_codec_idt 61482 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_hda_intel 25741 2 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_hda_codec 85759 3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_hwdep 6924 1 snd_hda_codec[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_pcm_oss 41394 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_mixer_oss 16299 1 snd_pcm_oss[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_pcm 87946 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_seq_dummy 1782 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_seq_oss 31191 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_seq_midi 5829 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_rawmidi 23420 1 snd_seq_midi[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]fbcon 39270 71 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_seq 57481 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_timer 23649 2 snd_pcm,snd_seq[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_seq_device 6888 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]tileblit 2487 1 fbcon[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]font 8053 1 fbcon[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd 71251 16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]lib80211_crypt_tkip 8676 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]bitblit 5811 1 fbcon[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]softcursor 1565 1 bitblit[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]soundcore 8052 1 snd[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]snd_page_alloc 8500 2 snd_hda_intel,snd_pcm[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]fglrx 2353486 35 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]dell_wmi 2177 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]uvcvideo 62819 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]videodev 40518 1 uvcvideo[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]btusb 13001 2 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]wl 1964968 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]dell_laptop 7941 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]vga16fb 12757 1 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]vgastate 9857 1 vga16fb[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]lp 9336 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]parport 37160 2 ppdev,lp[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]psmouse 64576 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]joydev 11104 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]v4l1_compat 15495 2 uvcvideo,videodev[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]intel_agp 29319 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]video 20623 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]dcdbas 6886 1 dell_laptop[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]bluetooth 58685 9 rfcomm,sco,bnep,l2cap,btusb[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]lib80211 6151 2 lib80211_crypt_tkip,wl[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]v4l2_compat_ioctl32 11892 1 videodev[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]output 2503 1 video[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]usbhid 41116 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]hid 83536 1 usbhid[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]serio_raw 4918 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ahci 37870 2 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]r8169 39714 0 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]mii 5237 1 r8169[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ lshw -C network[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]WARNING: you should run this program as super-user.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]*-network [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]description: Wireless interface[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]product: Broadcom Corporation[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]bus info: pci@0000:12:00.0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]logical name: eth1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]version: 01[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]serial: 1c:65:9d:79:b0:7e[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]capabilities: bus_master cap_list ethernet physical wireless[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]resources: irq:17 memory:fbd00000-fbd03fff[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]*-network[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]description: Ethernet interface[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]bus info: pci@0000:13:00.0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]logical name: eth0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]version: 02[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]serial: f0:4d:a2:aa:66:37[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]capabilities: bus_master cap_list rom ethernet physical[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]resources: irq:33 ioport:d000(size=256) memory:d0c10000-d0c10fff(prefetchable) memory:d0c00000-d0c0ffff(prefetchable) memory:fb300000-fb31ffff(prefetchable)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ iwlist scan[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]lo Interface doesn't support scanning.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]eth0 Interface doesn't support scanning.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]eth1 Interface doesn't support scanning.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]pan0 Interface doesn't support scanning.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ lsb_release[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]No LSB modules are available.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]~$ uname -mr[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]2.6.32-28-generic x86_64[/FONT][/SIZE]

 
By the way, the reason I post this here is because I got confused... I could not decide whether this is a 'wireless' problem or a '64 bit' problem. And I am an absolute beginner, so... If this is the wrong place, I apologise.
 
So... any suggestions? I really would like to try 64-bit linux, but I am lost with no internet. Hm, now that I think about it, I could just buy another cable and connect my laptop to my router, but it's not really a solution is it... the whole point of the laptop being mobility.
 
Also, the files I mentioned I removed from the /lib/firmware directory, should I move them back there? (I kept copies elsewhere.)

---

### Post by NJPinator on 2011-03-01
> **_niai said:**
> Also, the files I mentioned I removed from the /lib/firmware directory, should I move them back there? (I kept copies elsewhere.)

Yes, I think you should; most of these are "drivers". You see, Linux doesn't use separate drivers just for two different pieces of hardware -- it works out which driver to use based on it's chip model (can't remember if this is micro-processor or something else right now).

In addition, I haven't taken into account any of the logs you posted from the terminal, this is just some plain advice... connect via Ethernet and visit your manufacturer's website to see if they have a driver for your wireless card that is compatible with Linux. Or look for a community-made one (if possible). I'm kind of a beginner to hardware stuff as well, but if it is a software bug..it's most likely to do with your hardware not having its driver installed by default in Ubuntu. Also, go to [System > Administration > Additional Drivers] to see if the system can automatically locate drivers for you (be connected via Ethernet when you do this!)

---

### Post by _niai on 2011-03-01
> **NJPinator said:**
> Yes, I think you should; most of these are "drivers". You see, Linux doesn't use separate drivers just for two different pieces of hardware -- it works out which driver to use based on it's chip model (can't remember if this is micro-processor or something else right now).
Thank you, I will move them back when I get on my laptop again (kind of no use at the moment... I am looking for info online and going back and forth between the two desks got old really fast).
 
>  Also, go to [System > Administration > Additional Drivers] to see if the system can automatically locate drivers for you (be connected via Ethernet when you do this!)

The Broadcom driver was suggested, and I installed it. It worked ok with 32-bit Lucid, so... Heh, I guess it's never late to run out of luck.
 
Thank you for your reply.

---

### Post by _niai on 2011-03-03
Well, something must have worked.

I came back yesterday and turned on the laptop, and all of a sudden the wireless network was found and connected to with no action required from me. Weird.

Why this did not happen after a previous restart is beyond me. :?

---

### Post by NJPinator on 2011-03-04
Does your system automatically update? There was a kernel revision recently; that could've fixed the issue.

Anyhow, be sure to mark this thread as "Solved" so that others can come here for advice and to prevent inane posts! You can do this at the top of this page by selecting "Solved" from one of the drop-downs (I can't remember the name but it's pretty obvious...) ;)

---

### Post by _niai on 2011-03-04
> **NJPinator said:**
> Does your system automatically update? There was a kernel revision recently; that could've fixed the issue.

Anyhow, be sure to mark this thread as "Solved" so that others can come here for advice and to prevent inane posts! You can do this at the top of this page by selecting "Solved" from one of the drop-downs (I can't remember the name but it's pretty obvious...) ;)
I did it already :D Although it isn't actually clear what solved the problem, but I think I know somebody who can help me figure it out (it'd be easier talking face to face and with my laptop present), and when I do I will edit this, so it be known.

(And no, my system doesn't update automatically, I prefer to know when things are about to change and to choose these changes; and during the last use of my laptop previous to the start up followed by connecting to the wireless network I wasn't connected anyway, so an update couldn't have happened even if desired.)

---

