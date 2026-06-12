---
title: "Speedy Remote Desktop in Ubuntu?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by speedsix on 2008-06-25
I'm trying to connect to my works XP machine, rdesktop is very slow so I'm currently having to dual boot XP just to use RDP, which is much faster when using the native Windows client.

I have tried connecting my VPN in Ubuntu, starting up my XP virtual machine in VirtualBox (NAT mode) and attempting to use RDP there but it can't see the internal ips provided by the Linux host's VPN. You also can't use the Windows VPN connection because in NAT VirtualBox doesn't pass the GRE packets from the guest to the host.

I tried setting VirtualBox up to work in Host mode instead of NAT and creating the VPN connection in Windows itself but bridging with a WiFi card doesn't work so that idea went out the window.

Last attempt I tried installing the Windows RDP client in Wine 1.0 but this just kept crashing.

Any ideas?

Thanks

---

### Post by speedsix on 2008-07-05
Any ideas?

---

### Post by prshah on 2008-07-05
> **speedsix said:**
> Any ideas?

Can you consider installing VNC on your Windows work machine? See [www.realvnc.org](www.realvnc.org)

---

### Post by kevdog on 2008-07-05
FreeNX is another alternative -- its fairly fast.

---

