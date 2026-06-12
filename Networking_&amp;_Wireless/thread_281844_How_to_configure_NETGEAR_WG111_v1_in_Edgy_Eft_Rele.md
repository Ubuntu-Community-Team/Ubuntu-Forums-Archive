---
title: "How to configure NETGEAR WG111 v1 in Edgy Eft Release Candidate"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by sankarj12 on 2006-10-21
Hey.  I want to configure NETGEAR WG111 v1 on my Edgy Eft Release Candidate computer.  I have installed ndiswrapper-utils and when I enter ```
ndiswrapper -i netwg111.inf
``` I get ```
command not found
```  I think I need my source files for kernel, but I'm not sure.  Could anyone point me in the right direction?](*,)

---

### Post by sankarj12 on 2006-10-24
Anybody?

---

### Post by Jose Catre-Vandis on 2006-11-08
try
```
sudo ndiswrapper -i netwg111,inf
```

make sure that the driver and the sys file are in your home directory.

This said, i am having trouble getting v2 to work beyond this stage so report back on progress

---

### Post by olur on 2006-11-09
The netwg111.inf file is a Windows driver used by ndiswrapper, you can either get it from a Windowns installation, in the System32\drivers directory, or download it form Netgear. Good luck.

---

### Post by FrodoB on 2006-11-09
Jose;

The Netgear WG111v2 works out of the box in Edgy without ndiswrapper.

---

### Post by Jose Catre-Vandis on 2006-11-11
> **FrodoB said:**
> Jose;

The Netgear WG111v2 works out of the box in Edgy without ndiswrapper.

Yes, it does! now!

took me most of the afternoon to figure this one out but got there in the end

You need to have rtl8187 loaded for this to work:
```
 sudo modprobe r8187
```

I have vmware-server installed and this was confusing the driver. I was getting connected to the outer reaches of the router and the dhcp was giving me an address, but I was getting the following message:
```
SIOCADDRT: Network is unreachable
```
vmnet1 was getting in the way and picking up the dhcp before passing it on to wlan0.


I opened up system monitor, killed all vmnet/vmware processes that were running following boot, modprobed r8187 just to ensure it was loaded, plugged in the adapter and hey presto, connection. You don't get a blue light, but who cares :-)

FWIW this also occurs with my Corega USB Stick II (version 1) which has a prism2 chipset.

So must figure out how to stop all the vmware processes loading on boot, then write a script to load them before starting up vmware, unless someone knows a better way?  Or perhaps what needs to be done to prioritise wlan0 over vmnet1? ](*,) 

Sorry to hijack the thread a bit, but this should help you, sankarj12 :-)

---

