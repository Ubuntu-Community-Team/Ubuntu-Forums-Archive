---
title: "Trouble Setting up new 14.04 LTS server - router and/or devices?"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by warr87 on 2015-12-13
Hi all,

I have recently installed 14.04 LTS server edition and have been trying to get the system actually working. So far I have been left incredibly frustrated and not knowing what to do. It took a while to install it (I had some problems there using a USB but found a fix) and the problems haven't stopped there.

I have been trying to, at the very least, get my new server set up as headless so I can get everything else going--but I haven't even been able to do that. When I installed ubuntu I also installed OpenSSH and Samba along with it. My aim for this server is a NAS + media server. I was going to experiment with the media server stuff later as my primary objective is the NAS. Once that is up and going then I will look into tweaking other things.

This leads me to my first major problem--my server doesn't seen to recognise my router (Netis WF2780) or the install doesn't have the drivers for my ethernet connection. I'm not sure which one it is, or if it's both. The firmware on my router isn't the newest, but from comparing the version numbers it is still pretty new. And my MOBO is old enough to be supported .... so I thought. I also don't have an internet connection to use which the server since this will be a closed home setup for my devices (and where I live I can't get a proper connection. I've been using my phone's internet to try and find solutions for my current problem, and a mobile router that connects via USB for my internet connection). My ethernet port is from my MOBO ASRock FM2A88M EXTREME4+, (I get the code QCA8171 when I've been looking up my devices etc.), and is plugged into the back of my router with a cat6 cable. When I look at my network interfaces I only see, "lo", "vibr0", and depending on which command I use, "p19p1" (as it's 'logical name', which I understand is common with my MOBO's onboard ethernet device), thus I can't find "eth0" at all. When I looked at /etc/network/interfaces I only saw "lo" and nothing else. I dont have network-manager installed and I dont know how I can get my network going (can't connect to the internet with the server so I obviously can't install network-manager or other things). I've also logged into my router's admin page and can only see my windows system, not the server despite the fact that it is plugged in directly.

And without an internet connection at all I obviously had to skip the network setup during install. I thought the router would be PnP since it is supposed to be linux compatible. 

If you can't tell, I'm getting rather annoyed with what I thought would be relatively simple and straight forward. Any help would be appreciated, otherwise I got myself a rather large and expensive paperweight.

I understand you will need more info on my system, so please let me know what info I can pass to you guys/girls to hopefully solve the problem!

Thanks, I am eagerly awaiting responses!

Warr87

---

### Post by praseodym on 2015-12-13
Hi,

please show the outputs of these commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by warr87 on 2015-12-13
> Linux server 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 GNU/Linux

> 30:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1) (rev 10)
Subsystem: ASRock Incorporation Device [1849:10a1]
Kernel driver in use: alx

> xt_CHECKSUM 16384 1
iptable_mangle 16384 1
xt_tcpudp 16384 6
bridge 110592 0
stp 16384 1 bridge
llc 16384 2 stp,bridge
ip6table_filter 16384 0
ip6_tables 28672 1 ip6table_filter
iptable_filter 16384 1
ip_tables 28672 3 iptable_filter,iptable_mangle,iptable_net
ebtable_nat 16384 0
x_tables 36864 11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
ppdev 20480 0
kvm_amd 61440 0
kvm 479232 1 kvm_amd
crct10dif_pclmul 16384 0
crc32_pclmul 16384 0
ghash_clmulni_intel 16384 0
aesni_intel 172032 0
aes_x86_64 20480 1 aesni_intel
lrw 16384 1 aesni_intel
gf128mul 16384 1 lrw
glue_helper 16384 1 aesni_intel
ablk_helper 16384 1 aesni_intel
cryptd 20480 3 ghash_clulni_intel,aesni_intel,ablk_helper
serio_raw 16384 0
k10temp 16384 0
nls_iso8859_1
shpchp 40960 0
i2c_piix4 24576 0
joydev 20480 0
amdkfd 81920 1
amd_iommu_v2 20480 1 amdkfd
snd_hda_codec_realtek 81920 1
snd_hda_codec_generic 69632 1 snd_hda_codec_realtek
radeon 1552384 1
8250_f intek 16384 0
snd_hda_codec_hdmi 53248 1
parport_pc 32768 1
snd_hda_intel 32768 0
snd_hda_controller 32678 1 snd_hda_intel
video 20480 0
snd_hda_codec 143360 5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep 20480 1 snd_hda_codec
snd_pcm 106496 4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
mac_hid 16384 0
snd_timer 32768 1 snd_pcm
snd 86016 8  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
soundcore 16384 2 snd,snd_hda_codec
ttm 94208 1 raedon
drm_kms_helper 126976 1 raedon
drm 344064 4 ttm,drm_kms_helper,raedon
i2c_algo_bit 16384 1 raedon
lp 20480 0
parport 45056 3 lp,ppdev,parport_pc
pata_acpi 16384 0
hid_generic 16384 0
usbhid 53248 0
hid 110592 2 hid_generic,usbhid
psmouse 114688 0
alx 36864 0
mdio 16384 1 alx
ahci 36384 3
pata_atiixp 16384 0
libahci 32768 1 ahci

> 
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:44 errors:0 dropped:0 overruns:0 frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3200 (3.2 KB) TX bytes:3200 (3.2 KB)

p19p1 Link encap:Ethernet HWaddr d0:50:99:1a:88:ed
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0 B) TX bytes:0 (0 B)

virbr0 Link encap:Ethernet HWaddr ae:35:cf:dd:f8:59
inet addr:192.168.122.1 Bcast192.168.122.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets04 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0 B) TX bytes:0 (0 B)


> 
auto lo
iface lo inet loopback


> 
(just comments for cat /etc/resolv.conf, nothing actually in it but a warning not to edit by hand)



I hope this helps!!

---

### Post by praseodym on 2015-12-13
Ok, lets try:
```

echo "nameserver xxx.xxx.xxx.xxx" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
ifconfig -a
route -n
```Replace XXX.XXX.XXX.XXX with the IP address of your router

---

### Post by warr87 on 2015-12-13
Don't think it did anything to be honest. ifconfig -a looks the same. route -n gave me this:

Destination         Gateway     Genmask          Flags      Metric   Ref   Use   Iface
192.168.122.0      0.0.0.0      255.255.255.0    U           0         0      0     virbr0

---

### Post by warr87 on 2015-12-15
Any suggestions?

Should I try buying/installing a PCI card for my ethernet connection?

---

### Post by warr87 on 2015-12-21
Just to update for anyone who might have the same problem in the future.

I bought a cheap ethernet PCI card and just reinstalled (decided to use the new 15.10 edition). Everything went through perfectly. However, I tried going back to using the MOBO's ethernet port: QCA8171. This still wasn't working. Once I installed 'compat-drivers', now known as 'backports', it worked fine. So even though I had alx drivers installed and working, I needed the alx drivers from backport to actually get it working properly.

---

