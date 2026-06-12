---
title: "Marvell 88E8057 ethernet adapter not working"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by ThermoGel on 2014-04-17
Does the sky2 driver not work with Marvell ethernet adapters? I have tried Ubuntu 13.04 and with the sky2 driver it says that the cable is unplugged. In older versions of Ubuntu I was able to install the sk98lin driver from Marvell, but that will only work up to kernel 3.2.0. In the newest version of Ubuntu, Xbuntu or even Linux Mint the sk98lin driver will not complie with the newer kernel. The network cards work, I dual boot the machine with windows 7 and currently I am using Linux Mint with the 3.2.0-23 kernel. The sky2 driver doesn't work, but I can install the sk98lin driver. Is there a way to get the Marvell ethernet adapters working?

---

### Post by varunendra on 2014-04-19
There are a couple of driver parameters available with the sky2 driver which may possibly help. But they are potentially risky and may break the system (temporarily, as long as they are effective). So try them in temporary mode first. Here's how -

Open a terminal (Ctrl-Alt-T) and unload - reload the driver (with parameters this time) with the following commands -
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 **[COLOR="#800000"]disable_msi=1[/COLOR]**
```
This would be effective only until the next boot or next unload - reload cycle (without the parameter). If it helps, we can make it permanent. If not, try the next parameter as follows -
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 **[COLOR="#0000CD"]legacy_pme=1[/COLOR]**
```

You can also try them both at once -
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 **[COLOR="#800000"]disable_msi=1[/COLOR] [COLOR="#0000CD"]legacy_pme=1[/COLOR]**
```

If none of these help, please show us the outputs of -
```
sudo lshw -C network
sudo ethtool eth0
```
(you may have to install 'ethtool' beforehand with "sudo apt-get install ethtool")

---

