---
title: "Intel Wi-Fi 7 BE 200 - no way to make it work again after suspension in Ubuntu 24.10"
date: 2024-11-01
forum: Networking &amp; Wireless
---

### Post by riccd on 2024-11-01
So this is getting me crazy, brand new laptop HP Spectre x360 16", wireless network works awesome until I suspend Ubuntu. When I Iog back in again, Ubuntu can't find any wireless network to connect to. I tried all most common ways to restart the service and disable power saving on the interface but to no avail. Only rebooting restores full connectivity. 
Here is the output of the wireless info script when the interface is working: 
[https://www.dsrealizzazioni.it/share/wireless-info-working.txt](https://www.dsrealizzazioni.it/share/wireless-info-working.txt)
here after suspension of ubuntu and resume:
[https://www.dsrealizzazioni.it/share/wireless-info-off.txt](https://www.dsrealizzazioni.it/share/wireless-info-off.txt)

1-I think disabling the power saving on the interface could help.
2-but better would be to be able to correctly restart it after suspension.

---

### Post by riccd on 2024-11-02
After two days trying to solve this. I found a workaround.
> sudo nano /etc/default/grub
append pcie_port_pm=off to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_port_pm=off" 
and update GRUB
> sudo update-grub
Reboot and now you can suspend without losing your wifi.
The thing I don't like here is that from what I know many devices are connected to pcie, this means that all these devices will not be power managed anymore. Which is clearly not good. Anyone knows how to specify this only for wifi? 

I also have to mention one of the main log messages i was having: 
> iwlwifi: unable to change power state from D3cold to D0, device insaccessible 

---

### Post by riccd on 2024-11-09
/ehm sorry, bad message, you can delete this last reply

---

### Post by 1fallen on 2024-11-09
Not sure I can help, but I would like to see this please:
```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by riccd on 2024-11-09
> **1fallen said:**
> Not sure I can help, but I would like to see this please:
```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

[connection]
wifi.powersave = 3

I have played around with those settings for days and nothing worked unfortunately, it's something more deep. I was trying to find a better solution right now and found this repository
[https://github.com/aigilea/hp_spectre_x360_14_eu0xxx](https://github.com/aigilea/hp_spectre_x360_14_eu0xxx)
which deals exactly with these problems. This patch they provide [https://www.dsrealizzazioni.it/share/hp-spectre-x360-16-aa0xxx-f10.asl](https://www.dsrealizzazioni.it/share/hp-spectre-x360-16-aa0xxx-f10.asl) explains at the bottom where the problem lies. 
I just now applied the patch and it works. I don't know if you can get something interesting out of that patch. Thank you btw

For those who need it:
1-download the patch from the repository
2-compile it with iasl -tc hp-spectre-x360-16-aa0xxx-f10.asl
3-move the resulting .aml file to /boot
4-create a custom.cfg file in /boot/grub and add acpi /boot/hp-spectre-x360-16-aa0xxx-f10.aml 
5-reboot and disable secure boot. Now wifi should reload after suspension.

---

