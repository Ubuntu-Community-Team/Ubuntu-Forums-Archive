---
title: "edimax  usb wireless adapter from linux emporium problems"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by murphy25 on 2008-09-04
i bought a wireless usb adapter from the linux emporium as i couldnt get the one i already had to work.

the adapter is a Edimax 54 Mbps Wireless USB stick and it says on thier site and i quote -

"This card uses the RT2571 chipset and works "out of the box" with Ubuntu 8.04 Hardy Heron. It can be configured using Hardy's Network Manager to support both WEP and WPA encryption and in addition it's hot-pluggable. "

well any way it came this morning so i plugged it in disconnected the ethernet cable and booted up the laptop.
well here is my problem, in my network i have dhcp server disabled and assigned each computer a static ip,i am also using wpa encryption.
the adapter does connect if i enable the dhcp server in my router settings and enable roaming mode in network settings,but if i assign a static ip in network settings/wlan0 properties the icon on my toolbar turns back to the 2 monitors and if i left click on them it shows "wired connection" and "manual configuration". and if i right click it shows "enable natwork"(which is ticked) connection information(which is shaded out" "edit wireless networks" and "about" theres nothing about wireless networks.
so how can i assign the laptop a static ip using the network adapter and wpa encryption?????
any help would be welcome im a noob when it comes to ubuntu but i am learning fast.lol

---

### Post by freackout on 2008-09-05
> **murphy25 said:**
> i bought a wireless usb adapter from the linux emporium as i couldnt get the one i already had to work.

the adapter is a Edimax 54 Mbps Wireless USB stick and it says on thier site and i quote -

"This card uses the RT2571 chipset and works "out of the box" with Ubuntu 8.04 Hardy Heron. It can be configured using Hardy's Network Manager to support both WEP and WPA encryption and in addition it's hot-pluggable. "

well any way it came this morning so i plugged it in disconnected the ethernet cable and booted up the laptop.
well here is my problem, in my network i have dhcp server disabled and assigned each computer a static ip,i am also using wpa encryption.
the adapter does connect if i enable the dhcp server in my router settings and enable roaming mode in network settings,but if i assign a static ip in network settings/wlan0 properties the icon on my toolbar turns back to the 2 monitors and if i left click on them it shows "wired connection" and "manual configuration". and if i right click it shows "enable natwork"(which is ticked) connection information(which is shaded out" "edit wireless networks" and "about" theres nothing about wireless networks.
so how can i assign the laptop a static ip using the network adapter and wpa encryption?????
any help would be welcome im a noob when it comes to ubuntu but i am learning fast.lol

Did you do upgrade from 7.10 to 8.04 or fresh 8.04. i've noticed that with rolling distros changes are made + the cd given states drivers for lower distro numbers.. also sourceforge gives drivers (modules) quoted as 2570 not 2571 ie the extra arial ? try modules loaded (module-assistant) or adding (restricted-headers or linux-headers (uname-r)) mine seems to almost work (hotplugged without any driver installed as yet) but i'm from the upgrade path in addition to built in bcom primary wireless, settings ie was just testing the usb model as a curiosity to live distros working out of the box u c. also sourceforge states kernel 2.6.22 i think. Also RutilT or ndisgtk may help you out if you are stuck. Other graphical stuff usefull is madwifi i also believe you may need to install also wireless-tools or wlassistant depending on gnome or kde hmmm. hopes this helps.

---

