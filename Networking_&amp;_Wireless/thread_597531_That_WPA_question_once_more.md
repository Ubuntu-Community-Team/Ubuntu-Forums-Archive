---
title: "That WPA question once more"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by bobhunt on 2007-10-30
Hi,

I've searched the forums here and the web with no solid answer (or answer that gets me anywhere in my particular case), so I was hoping someone might have a straight answer for me:

I have installed 7.04, it has picked up my Linksys WMP54G wireless card and when I click the network icon in the top toolbar it displays my local (home) SSID, which when I click only offers me various WEP options.

My router uses WPA, which, when I boot to Windows, all works fine.

The signal strength in windows is Excellent (quoted), in Ubuntu it is showing as 30% when I hover the icon  in the top toolbar and 0% when I go to Network Manager.

Thank you for any help.

---

### Post by dacap06 on 2007-10-30
Signal strength in Ubuntu typically shows very low to nothing at all when you are not connected to a WAP that uses WPA.   I will proceed from here under the assumption that you do not have WPA working.

1)  You need to install the wpasupplicant package.

2) You need to create by hand a wpa supplicant configuration file in the /etc/ directory.  Luckily, there is a template in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.template.  Copy it to /etc/wpa_supplicant.conf, then edit it and put in values that are sensible for your system.  The README file is most helpful in deciding what is sensible.  For a home server, use a pre-shared key.  

My version of this config file is shown below (minus my key).  By setting up my home network (ID=42) first, then adding one with no encryption, it looks for mine and if it can't find it looks for any unencrypted network.  This enables my laptop work at home and at the coffee shop.

========================================================================
ctrl_interface=/var/run/wpa_supplicant
update_config=1

network={
	ssid="42"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="<put your key in here>"
}

network={
	key_mgmt=NONE
}
========================================================================

3) I used kwlan in 7.04 to activate WPA on my specific network.  That did not work for me at all in 7.10 and I was forced to add the following line to my init script /etc/init.d/rc.local in the START section to get WPA started:

/sbin/wpa_supplicant -B -iath0 -c/etc/wpa_supplicant.conf

Be sure to change the wireless interface (ath0 in my case) to be whatever device name you use.

---

