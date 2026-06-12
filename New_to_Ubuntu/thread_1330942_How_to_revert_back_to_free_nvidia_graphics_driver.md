---
title: "How to revert back to free nvidia graphics driver?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2009-11-18
I'm on 8.10 Ibex and I tried to install the nvidia driver (through hardware manager & through Synaptic). When I rebooted it hadn't worked and ubuntu defaulted to the present extremely basic video driver. (I now know it doesn't work, from [here]("http://www.ubuntu.com/getubuntu/releasenotes/810")).

How do I revert back to the normal default free nvidia driver?

```
user@user:~$ lspci | grep -i nvidia

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
```

Ubuntu 8.10

---

### Post by stlsaint on 2009-11-18
try unactivating all other video drivers via System>Admin>Hardware Drivers

---

### Post by sandyd on 2009-11-18
> **Mega_Fauna said:**
> I'm on 8.10 Ibex and I tried to install the nvidia driver (through hardware manager & through Synaptic). When I rebooted it hadn't worked and ubuntu defaulted to the present extremely basic video driver. (I now know it doesn't work, from [here]("http://www.ubuntu.com/getubuntu/releasenotes/810")).

How do I revert back to the normal default free nvidia driver?

```
user@user:~$ lspci | grep -i nvidia

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
```Ubuntu 8.10
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Mega_Fauna on 2009-11-18
> **stlsaint said:**
> try unactivating all other video drivers via System>Admin>Hardware Drivers

The button was greyed out so I hadn't clicked it, but I did all the same and it did click and after a reboot, my system is up and running again. Thanks!

/feel like such a newb

---

