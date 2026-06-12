---
title: "RT5370 Wireless Adapter, 14.04"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by joshua43 on 2015-02-26
I'm working on getting a usb wifi adapter working in Ubuntu 14.04 (using Vagrant and VirtualBox). The adapter is the [Panda 802.11 USB Adapter]("http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG") and on the Q&A section on Amazon, it states: this device is "plug-n-play" in 14.04 and that "[COLOR=#000000][FONT=Arial]*this device uses a **RaLink** chipset. For **Linux** it needs the kernel module rt5370sta*".

I don't believe the kernel module mentioned above is loading for me. 

Can anyone please help me to get this device working? I want to use it to create a WAP.

[/FONT][/COLOR][B]lsb_release -a
[/B]```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

```
[COLOR=#000000][FONT=Arial][B]lsusb
[/B][/FONT][/COLOR]```
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
[COLOR=#000000][FONT=Arial]
**Modprob**
[/FONT][/COLOR]```

modprobe: FATAL: Module rt5370sta not found.

```
[B]
lsmod
[/B]```
Module                  Size  Used by
vboxsf                 43786  0 
nfsd                  280289  2 
auth_rpcgss            59338  1 nfsd
nfs_acl                12837  1 nfsd
nfs                   236726  0 
lockd                  93977  2 nfs,nfsd
sunrpc                289260  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                63988  1 nfs
dm_crypt               23177  0 
ppdev                  17671  0 
serio_raw              13462  0 
parport_pc             32701  0 
parport                42348  2 ppdev,parport_pc
video                  19476  0 
vboxguest             248441  2 vboxsf
psmouse               106714  0 
ahci                   29915  1 
libahci                32716  1 ahci
e1000                 145174  0 

```

[B]iwconfig
[/B]```
eth0      no wireless extensions.


lo        no wireless extensions.

```

---

### Post by joshua43 on 2015-02-27
Bumping this so hopefully someone has some thoughts. I've looked through tons of other similar threads and have tried many things, but they don't seem to be working.

---

