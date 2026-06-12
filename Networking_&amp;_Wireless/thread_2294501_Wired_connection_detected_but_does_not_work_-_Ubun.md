---
title: "Wired connection detected but does not work - Ubuntu 14.04"
date: 2015-09-11
forum: Networking &amp; Wireless
---

### Post by andretahim on 2015-09-11
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I recently installed Ubuntu 14.04 on a desktop at my university and I will only use wired connection. This connection works great on windows 7 in the same PC. I was looking for solutions and I saw many commands that might be useful for advanced users to help me out. I would appreciate any advice. Thanks in advance.[/COLOR]

```

[COLOR=#000000]~$ ifconfig -a[/COLOR]
[COLOR=#000000]eth0 Link encap:Ethernet HWaddr 10:c3:7b:c4:60:be [/COLOR]
[COLOR=#000000]inet addr:192.168.174.119 Bcast:192.168.174.255 Mask:255.255.255.0[/COLOR]
[COLOR=#000000]inet6 addr: fe80::12c3:7bff:fec4:60be/64 Scope:Link[/COLOR]
[COLOR=#000000]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=#000000]RX packets:2270 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=#000000]TX packets:89 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=#000000]collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=#000000]RX bytes:367221 (367.2 KB) TX bytes:10675 (10.6 KB)[/COLOR]


[COLOR=#000000]lo Link encap:Local Loopback [/COLOR]
[COLOR=#000000]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=#000000]inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=#000000]UP LOOPBACK RUNNING MTU:65536 Metric:1[/COLOR]
[COLOR=#000000]RX packets:93 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=#000000]TX packets:93 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=#000000]collisions:0 txqueuelen:0 [/COLOR]
[COLOR=#000000]RX bytes:8191 (8.1 KB) TX bytes:8191 (8.1 KB)[/COLOR]




[COLOR=#000000]~$ netstat -rn[/COLOR]
[COLOR=#000000]Kernel IP routing table[/COLOR]
[COLOR=#000000]Destination Gateway Genmask Flags MSS Window irtt Iface[/COLOR]
[COLOR=#000000]0.0.0.0 192.168.174.1 0.0.0.0 UG 0 0 0 eth0[/COLOR]
[COLOR=#000000]169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0[/COLOR]
[COLOR=#000000]192.168.174.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0[/COLOR]




[COLOR=#000000]~$ ip route show[/COLOR]
[COLOR=#000000]default via 192.168.174.1 dev eth0 [/COLOR]
[COLOR=#000000]169.254.0.0/16 dev eth0 scope link metric 1000 [/COLOR]
[COLOR=#000000]192.168.174.0/24 dev eth0 proto kernel scope link src 192.168.174.119 [/COLOR]






[COLOR=#000000]~$ sudo vi /etc/network/interfaces[/COLOR]
[COLOR=#000000]# interfaces(5) file used by ifup(8) and ifdown(8)[/COLOR]
[COLOR=#000000]auto lo[/COLOR]
[COLOR=#000000]iface lo inet loopback[/COLOR]


[COLOR=#000000]~$ sudo lshw |grep -ia2 net[/COLOR]
[COLOR=#000000]configuration: driver=pcieport[/COLOR]
[COLOR=#000000]resources: irq:18 ioport:e000(size=4096) ioport:f0000000(size=1048576)[/COLOR]
[COLOR=#000000]*-network[/COLOR]
[COLOR=#000000]description: Ethernet interface[/COLOR]
[COLOR=#000000]product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/COLOR]
[COLOR=#000000]vendor: Realtek Semiconductor Co., Ltd.[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]--[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/COLOR]
[COLOR=#000000]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.174.119 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s[/COLOR]
[COLOR=#000000]resources: irq:27 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
[/COLOR]
```

---

### Post by TheFu on 2015-09-11
Not certain I'm reading the output correctly. I'm old and haven't used the 'ip' cmds, ever.
Please post a simple **route** output.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has more ideas.

---

### Post by andretahim on 2015-09-11
> **TheFu said:**
> Not certain I'm reading the output correctly. I'm old and haven't used the 'ip' cmds, ever.
Please post a simple **route** output.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has more ideas.



```

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.174.1   0.0.0.0         UG    0      0        0 eth0
192.168.174.0   *               255.255.255.0   U     1      0        0 eth0

```

---

### Post by TheFu on 2015-09-11
Thanks.
That looks fine - so does everything else.  Try the different ping tests, in order, in the link above and report what works and what doesn't.

---

### Post by ajgreeny on 2015-09-11
Try command ```
ping 216.58.208.46
```and then ```
ping google.com
``` If the first works but the second fails it will tell us if you have a DNS problem and we can take it further from there.

---

### Post by praseodym on 2015-09-11
Download these files and save them in "Downloads":

[http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by andretahim on 2015-09-11
Hi TheFu,

the link does not work for me (403 Forbidden). I am going to try the other advices.

---

### Post by andretahim on 2015-09-11
> **ajgreeny said:**
> Try command ```
ping 216.58.208.46
```and then ```
ping google.com
``` If the first works but the second fails it will tell us if you have a DNS problem and we can take it further from there.

The results I got are the same:

```

~$ ping 216.58.208.46
PING 216.58.208.46 (216.58.208.46) 56(84) bytes of data.
From 192.168.174.119 icmp_seq=1 Destination Host Unreachable
From 192.168.174.119 icmp_seq=2 Destination Host Unreachable
From 192.168.174.119 icmp_seq=3 Destination Host Unreachable
From 192.168.174.119 icmp_seq=4 Destination Host Unreachable
From 192.168.174.119 icmp_seq=5 Destination Host Unreachable
From 192.168.174.119 icmp_seq=6 Destination Host Unreachable
^C
--- 216.58.208.46 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6031ms
pipe 3
tahim@tahim-desktop:~$ ping www.google.com
ping: unknown host www.google.com

```

---

### Post by andretahim on 2015-09-11
> **praseodym said:**
> Download these files and save them in "Downloads":

[http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot


Hi,

I did this, but nothing has changed! Thanks...

---

### Post by TheFu on 2015-09-11
> **andretahim said:**
> Hi TheFu,

the link does not work for me (403 Forbidden). I am going to try the other advices.

Which browser?

I don't know where in the world you are coming from, but Thailand, India, Pakistan have blocked my blog for a few years. Oddly, countries from the middle East and other Asian countries do not.  Of course, I haven't visited every country in the world, but that is my plan. ;)

If you can't ping the local router, the issue is:
* the drivers
* the network card
* the cable
* the port on the router/switch

```
sudo lshw -C network
``` will let us see the current driver.

---

### Post by praseodym on 2015-09-11
Lets check now:
```

lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dkms status
```

---

### Post by andretahim on 2015-09-14
> **praseodym said:**
> Lets check now:
```

lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dkms status
```


Hi,

I could not answer earlier because it is a computer from the university. Thanks.
```

tahim@tahim-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1 
rfcomm                 69632  0 
bnep                   20480  2 
bluetooth             491520  10 bnep,rfcomm
uas                    24576  0 
usb_storage            69632  2 uas
joydev                 20480  0 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    81920  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
snd_hda_intel          32768  5 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
snd_hda_controller     32768  1 snd_hda_intel
intel_powerclamp       20480  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
coretemp               16384  0 
snd_hwdep              20480  1 snd_hda_codec
kvm                   479232  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
i915                 1048576  4 
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                24576  0 
mei_me                 20480  0 
shpchp                 40960  0 
mei                    90112  1 mei_me
soundcore              16384  2 snd,snd_hda_codec
drm_kms_helper        126976  1 i915
drm                   344064  5 i915,drm_kms_helper
i2c_algo_bit           16384  1 i915
wmi                    20480  1 asus_wmi
8250_fintek            16384  0 
video                  20480  2 i915,asus_wmi
tpm_infineon           20480  0 
mac_hid                16384  0 
parport_pc             32768  1 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
r8168                 516096  0 
psmouse               114688  0 
r8169                  81920  0 
ahci                   36864  2 
libahci                32768  1 ahci
mii                    16384  1 r8169




tahim@tahim-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:c3:7b:c4:60:be  
          inet addr:192.168.174.119  Bcast:192.168.174.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fec4:60be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:178551 (178.5 KB)  TX bytes:15803 (15.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52167 (52.1 KB)  TX bytes:52167 (52.1 KB)






tahim@tahim-desktop:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




tahim@tahim-desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search dee.intranet.ufba.br




tahim@tahim-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.174.1   0.0.0.0         UG    0      0        0 eth0
192.168.174.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0




tahim@tahim-desktop:~$ dkms status
r8168-dkms, 8.040.00, 3.19.0-25-generic, x86_64: installed (WARNING! Diff between built and installed module!)



```

---

### Post by TheFu on 2015-09-14
You left out the most important things - is it working or not?

Also, I've asked for lshw output with specific options.
You should try these things in order and report the results:
* ping the router by IP
* ping a few well-known internet addresses by IP
* ping a few well-known interent addresses by DNS names
Please show your work. These simple tests tell us so many thing things.

---

### Post by andretahim on 2015-09-14
> **TheFu said:**
> Which browser?

I don't know where in the world you are coming from, but Thailand, India, Pakistan have blocked my blog for a few years. Oddly, countries from the middle East and other Asian countries do not.  Of course, I haven't visited every country in the world, but that is my plan. ;)

If you can't ping the local router, the issue is:
* the drivers
* the network card
* the cable
* the port on the router/switch

```
sudo lshw -C network
``` will let us see the current driver.

Hi TheFu,
I am from Brazil. I really don't know why I can not access your blog. Thanks
```

tahim@tahim-desktop:~$ sudo lshw -C network
[sudo] password for tahim: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 09
       serial: 10:c3:7b:c4:60:be
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.174.119 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:27 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff



```

---

### Post by TheFu on 2015-09-14
The **driver=r8169** output shows the blacklist failed.
This didn't happen or didn't work.
```
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Try again.

I haven't been to Brazil yet (it is on my list), but from Uruguay and Argentina, no issues.
Try google's cache or the "wayback" machine - just search for that. This should work with any website blocked that is mostly static.

Also, try a different browser.  Some of the newer browsers have issues - I know Win10's built-in browser doesn't work. I'll do some research to see if a work-around exists.

---

### Post by andretahim on 2015-09-14
> **TheFu said:**
> You left out the most important things - is it working or not?

Also, I've asked for lshw output with specific options.
You should try these things in order and report the results:
* ping the router by IP
* ping a few well-known internet addresses by IP
* ping a few well-known interent addresses by DNS names
Please show your work. These simple tests tell us so many thing things.


Hi TheFu,

I am sorry... but I have to make all the tests and restart the computer on windows to post the results. Thanks a lot.

```

tahim@tahim-desktop:~$ ping 192.168.174.119
PING 192.168.174.119 (192.168.174.119) 56(84) bytes of data.
64 bytes from 192.168.174.119: icmp_seq=1 ttl=64 time=0.030 ms
64 bytes from 192.168.174.119: icmp_seq=2 ttl=64 time=0.036 ms
64 bytes from 192.168.174.119: icmp_seq=3 ttl=64 time=0.037 ms
64 bytes from 192.168.174.119: icmp_seq=4 ttl=64 time=0.040 ms
64 bytes from 192.168.174.119: icmp_seq=5 ttl=64 time=0.038 ms
64 bytes from 192.168.174.119: icmp_seq=6 ttl=64 time=0.041 ms
64 bytes from 192.168.174.119: icmp_seq=7 ttl=64 time=0.036 ms
64 bytes from 192.168.174.119: icmp_seq=8 ttl=64 time=0.039 ms
^C
--- 192.168.174.119 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6998ms
rtt min/avg/max/mdev = 0.030/0.037/0.041/0.004 ms
tahim@tahim-desktop:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.174.119 icmp_seq=1 Destination Host Unreachable
From 192.168.174.119 icmp_seq=2 Destination Host Unreachable
From 192.168.174.119 icmp_seq=3 Destination Host Unreachable
From 192.168.174.119 icmp_seq=4 Destination Host Unreachable
From 192.168.174.119 icmp_seq=5 Destination Host Unreachable
From 192.168.174.119 icmp_seq=6 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5999ms
pipe 4
tahim@tahim-desktop:~$ ping 64.233.160.0
PING 64.233.160.0 (64.233.160.0) 56(84) bytes of data.
From 192.168.174.119 icmp_seq=1 Destination Host Unreachable
From 192.168.174.119 icmp_seq=2 Destination Host Unreachable
From 192.168.174.119 icmp_seq=3 Destination Host Unreachable
From 192.168.174.119 icmp_seq=4 Destination Host Unreachable
From 192.168.174.119 icmp_seq=5 Destination Host Unreachable
From 192.168.174.119 icmp_seq=6 Destination Host Unreachable
^C
--- 64.233.160.0 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6032ms
pipe 3
tahim@tahim-desktop:~$ ping 139.130.4.5
PING 139.130.4.5 (139.130.4.5) 56(84) bytes of data.
From 192.168.174.119 icmp_seq=1 Destination Host Unreachable
From 192.168.174.119 icmp_seq=2 Destination Host Unreachable
From 192.168.174.119 icmp_seq=3 Destination Host Unreachable
From 192.168.174.119 icmp_seq=4 Destination Host Unreachable
From 192.168.174.119 icmp_seq=5 Destination Host Unreachable
From 192.168.174.119 icmp_seq=6 Destination Host Unreachable
^C
--- 139.130.4.5 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7040ms
pipe 3
tahim@tahim-desktop:~$ ping google.com
ping: unknown host google.com
tahim@tahim-desktop:~$ ping www.google.com
ping: unknown host www.google.com
tahim@tahim-desktop:~$ ping yahoo.com
ping: unknown host yahoo.com



```

---

### Post by TheFu on 2015-09-14
192.168.174.1 is the router?  Ping that?

Pinging yourself, 192.168.174.119, shows a little, but not much.

---

### Post by andretahim on 2015-09-14
> **TheFu said:**
> 192.168.174.1 is the router?  Ping that?

Pinging yourself, 192.168.174.119, shows a little, but not much.


 Sorry, my router is 192.168.174.1

```

tahim@tahim-desktop:~$ ping 192.168.174.1
PING 192.168.174.1 (192.168.174.1) 56(84) bytes of data.
From 192.168.174.119 icmp_seq=1 Destination Host Unreachable
From 192.168.174.119 icmp_seq=2 Destination Host Unreachable
From 192.168.174.119 icmp_seq=3 Destination Host Unreachable
From 192.168.174.119 icmp_seq=4 Destination Host Unreachable
From 192.168.174.119 icmp_seq=5 Destination Host Unreachable
From 192.168.174.119 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.174.1 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7041ms
pipe 3

```

I am going to buy some networking for dummies book... it is the best way. At least I will provide valuable information to you. Thanks.

---

### Post by praseodym on 2015-09-14
> ```
search dee.intranet.ufba.br
```
Is this your domain?

---

### Post by andretahim on 2015-09-14
> **praseodym said:**
> Is this your domain?

Hi Praseodym, you are right.

This computer is part of the network of electrical engineering department (dee) of the Federal University of Bahia (UFBA) - (dee.intranet.ufba.br). There is a big strike right now, that's why I don't get any help from the IT group.

---

### Post by TheFu on 2015-09-14
Have you fixed the blacklist issue?  Until that is solved, I don't think it will work. 

While a networking for dummies won't hurt, it won't help here either.

If the same machine running Windows **with the same IP** can ping the router and it cannot with the identical IP under Linux, then the problem is a driver issue.  Right?

Are there other Linux machines on the same subnet?  Does the IT department require Active Directory logins and authentication to be on that subnet?  Some places do - but I've never seen that at any University.

1) fix the blacklist issue - that is the most important thing.

---

### Post by andretahim on 2015-09-14
Thank you so much TheFu,

I will try to fix it and I will post the results later.

All the best,

---

