---
title: "best solution for Asus wl 138g v2"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by frj on 2008-07-11
Hi,

I have recently purchased a Asus WL 138g V2 wireless cards for use in my Kubuntu Hardy amd64 box. 

The card was detected automatically and associated with the b43 and ssd driver. I did not do any tests only noticed that iwconfig listed the card. 
I assumed that in order to get WPA support i need to run it via ndiswrapper. 

So i got latest ndiswrapper from their homepage and installed it and installed the windows driver. I have not had any success with ndiswrapper yet. Anyway now when i have done my homework regarding this card i think that b43 driver should work with wpa_supplicant and -Dwext. Correct or incorrect? Any pros/cons with b43 compared to ndiswrapper and win driver? 

When i was working with ndiswrapper to get it working i noticed that Asus has a Linux driver on their homepage. Would that be the best way to go or is it better to go for the b43 driver. B43 should be native and open source. 

Or is ndiswrapper the best way to go anyway? If so do you think i might have greater success with the 64-bit driver for Vista? 

I want to be able to run WPA and i would like the card to be as stable as possible. Which of the available paths do you think is best? 

Frj

---

### Post by frj on 2008-07-13
anyway i decided to go for b43 and wpa_supplicant using wext driver. It works like a charm. But the only problem is that when i do a reboot the WLAN is not brought up automatically, or at least it does not acquire a DHCP lease. 

I have added the following to /etc/network/interfaces:```

auto wlan0
iface wlan0 inet dhcp
	wireless-essid malik
	wpa-driver wext
	wpa-conf /etc/wpa_supplicant.conf
```
This is my wpa_supplicant.conf ```
network={
	ssid="malik"
	proto=WPA
	key_mgmt=WPA-PSK
	psk=##HASH##
}
```
This should be sufficient in order to bring my wlan up and running? What i have do to is to manually run dhclient wlan0. My guess is that there is some interference with gnome-network-manager. Because i noticed that both eth0 and wlan0 was up after my reboot, both had ip adresses but no connectivity. eth0 is commented out in /etc/network/interfaces and cable unplugged, so contact with dhcp server is not possible. 
Trying to uninstall network-manger-gnome now. Then try a reboot. Get back to you soon.

Update, i removed netowrk-manager-gnome. Everything works now. So support for Asus WL 138g V2 is quite much OOB in Ubuntu, though you have to upgrade firmware. As long as you avoid any problems with network-managers.

---

