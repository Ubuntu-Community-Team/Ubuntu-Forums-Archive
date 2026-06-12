---
title: "wireless (wlan0) not visible in Linux Mint"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by amitabhishek on 2008-08-09
I am facing this peculiar problem, I am unable to see my wireless LAN in Network Manager (nm-applet), I mean its only eth0! 

When I go to network manager I can only see "Wired Connection" wireless has disappeared.

My ndiswrapper -l output shows this :

**[PHP][/PHP]net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)[PHP][/PHP]**

I use Acer aspire 4520, earlier I had a fully functional wireless.

iwconfig output is:

**[PHP][/PHP]sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[PHP][/PHP]**




I don't understand what could be the reason!!! Kindly help.

---

### Post by caljohnsmith on 2008-08-09
> **amitabhishek said:**
> My ndiswrapper -l output shows this :
net5211 : driver installed
        device (168C:001C) present ([COLOR="Red"]alternate driver: ath_pci[/COLOR])

It looks like Linux Mint is using the ath_pci module for your wireless card instead of your Windows driver with ndiswrapper. Open up your module blacklist file and see if "ath_pci" is in there:
```
gksudo gedit /etc/modprobe.d/blacklist
```
If it isn't add "blacklist ath_pci" at the bottom, save, reboot, and see if your wlan0 shows up after that.

---

### Post by amitabhishek on 2008-08-09
It works now! :):) Thanks a tonne!

---

