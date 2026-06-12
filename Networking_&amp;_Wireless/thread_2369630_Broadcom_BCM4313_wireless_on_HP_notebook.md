---
title: "Broadcom BCM4313 wireless on HP notebook"
date: 2017-08-25
forum: Networking &amp; Wireless
---

### Post by andyhelloween on 2017-08-25
Hello there,

This is yet another request for help on BCM4313.

I run Kubuntu 16.04 and suddenly wireless stop working. Apparently due to a hard block of the wireless. I checked BIOS and it's ON.

```

rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

```

lspci -nnk | grep 0280 -A2
0a:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
        DeviceName: Broadcom Valentine 802.11bgn 1x1 Combo
        Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless Network Adapter [103c:1795]

```

To cut the story short, I narrowed it down to **hp-wmi** kernel module. And here's the strange bit: The system starts with no wireless and works after I execute:

```

modprobe -r hp-wmi
modprobe hp-wmi
modprobe -r hp-wmi

```

End result is hp-wmi being removed, but I have no idea why it doesn't work on first try.
The module in question is also blacklisted:

```

:~$ cat /etc/modprobe.d/blacklist.conf | grep hp-wmi
blacklist hp-wmi
:~$ 

```

I resort to put those lines into a script for the time being. And after execution: ta-daaah...

```

rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

Does anyone know what to do/try out next to make it permanent?

Cheers,
Andres.

---

### Post by Hadaka on 2017-08-25
Hi, you could try..
```
sudo rm -rf  hp-wmi
```
you dont need the "modprobe" part.
Please also run the wireless script and let us have a look.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
Thanks.

---

### Post by discrimenthium on 2017-10-25
> **Hadaka said:**
> Hi, you could try..
```
sudo rm -rf  hp-wmi
```
you dont need the "modprobe" part.
Please also run the wireless script and let us have a look.
```
wget -N -t 5 -T 10  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info  && chmod +x wireless-info && ./wireless-info
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
Thanks.

Hi! I have same problem on linux mint 18.2. i have try this command and attached a file with output. I ask for help, as you can.

---

