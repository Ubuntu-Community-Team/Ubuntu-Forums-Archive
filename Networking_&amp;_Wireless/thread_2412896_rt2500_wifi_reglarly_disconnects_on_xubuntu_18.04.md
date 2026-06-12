---
title: "rt2500 wifi reglarly disconnects on xubuntu 18.04"
date: 2019-02-18
forum: Networking &amp; Wireless
---

### Post by pharbour on 2019-02-18
Hi,

After upgrading to xubuntu 18.04 from Ubuntu 14.04 my Ralink RT2500 (rt2500pci) wireless card regularly disconnects from the internet.  The disconnect appears to be directly related to power management of the Wifi PCI card.  The network link can be repaired by issuing
sudo ifconfig wlp4s2 down
sudo ifconfig wlp4s2 up
I have run wireless-info when the link is down, it is attached.
I have attempted to permanently correct the wifi disconnects by adjusting 
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 
wifi.powersave = 2      (turn wifi power management off)

Making this startup change causes the desktop panel autostart process to freeze (I believe it is freezing near the call of either nm-applet or xfce4-power-manager).  This changes hangs the GUI OS from starting and I must then 
a) revert changes to /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf (wifi.powersave = 3)
b) reboot in recovery mode 
c) manually start the network from recovery mode and allow its initial launch attempt to time out
before network access is recovered.

I should mention my xubuntu 18.04 LTS installation uses a pre-existing /home drive (which was previously configured with Ubuntu 14.04 running Gnome desktop).  I am unsure if pre-existing settings within the /home drive are negatively affecting desktop panel startup.  I understand 18.04 uses systemd from startup whereas 14.04 used upstart.  I'm not sure if I should make any changes to properly configure the wifi card with run with power-management=OFF.
I want to understand how to adjust the power management settings for the wifi card that cause the network service to regularly disconnect.
Please let me know which steps I should take to repair.


Thanks,

Pete

---

