---
title: "Intel AX210/AX211/AX411 often loses access to hardware device"
date: 2024-04-04
forum: Networking &amp; Wireless
---

### Post by k20shores on 2024-04-04
After I boot up Ubuntu, I often lose wifi within 10 minutes. This happens because the wifi device cannot get access to the wifi hardware (see the [dmesg log]("https://pastebin.com/MaRgNbUc")). Windows is installed on another NVME


What I've tried:
[LIST]
[*]sudo vim /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf and set wifi.powersave=2
[*][Disabling a iwlwifi driver]("https://askubuntu.com/questions/1435352/wi-fi-6-ax210-ax211-ax411-160mhz-no-longer-available/1435354#1435354") (still disabled)
[*]Disabled fast startup and hybrid shutdown in windows
[*]When the wifi fails, restarting the network manager (sudo systemctl restart NetworkManager.service). A little red icon with a white bar appears in place of where the wifi symbol is and no output is printed to the terminal and still no wifi
[*]Updating my BIOS
[*]Installed the [Intel® Wi-Fi 6 AX210 160MHz driver from this site]("https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html"), though it appears a different driver is still in use (specifically ty-a0-gf-a0-83.uc)
[/LIST]

Not sure what else to do. Here's a pastebin of the wifi info
[LIST]
[*][When it works]("https://paste.ubuntu.com/p/nFFDBtVXNG/")
[*][When it doesn't work]("https://pastebin.com/neQ4eMws")
[*][And a dmesg log of when it has failed]("https://pastebin.com/MaRgNbUc")
[/LIST]

---

### Post by jeremy31 on 2024-04-05
Edit /etc/default/grub and add ```
pcie_port_pm=off pcie_aspm.policy=performance
``` so it looks
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_port_pm=off pcie_aspm.policy=performance"
```
Save and exit then ```
sudo update-grub
```
Reboot

---

