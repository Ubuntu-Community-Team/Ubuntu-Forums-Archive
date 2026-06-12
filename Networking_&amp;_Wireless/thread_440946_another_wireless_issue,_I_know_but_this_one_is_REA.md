---
title: "another wireless issue, I know but this one is REAL"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by jarda-wien on 2007-05-12
first of all I'd like to say, that I used the search function, googled for the answer as well... I have been working on that over a month now!

My problem is that my network disconnects after a few seconds usind the madwifi driver. I tried to remove the linux-restricted package and build the newest drivers from svn. It still behaves the same way! Using ndiswrapper would be a nice suggestion, BUT it happens even with ndiswrapper and besides that, with Feisty, ndiswrapper freezes the system randomly. I tried other distros as well, debian stable and unstable, older versions of ubuntu and fedora core. Every distribution has the same problem, except for the ndiswrapper issue. I tried all possible combinations of ap_scan,fast_reauth and eapol version.
My router is an OvisLink configured to use WPA2-AES. I have a IBM ThinkPad T41 notebook with an atheros based card. I am pretty sure that the card is ok since wireless works flawlessly under winxp.
I have found a solution thou! If there is any network activity my system stays connected. So I just have to ping somewhere after ifup. Don't tell me this is only way to get working:lolflag: 

Thereis also another problem with Fn-F5 with ath_pci loaded it doesn't do anything. When I unload this module it switches bluetooth on and off like it should...

/etc/wpa_supplicant.conf
> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=0

network={
	ssid="jarda-wien"
	psk=password
	proto=WPA2
	key_mgmt=WPA-PSK
	auth_alg=OPEN
	pairwise=CCMP
	group=CCMP
	}

network={
        ssid="eduroam"
        key_mgmt=WPA-EAP
        eap=PEAP
        identity="user"
        password="password"
        ca_cert="/etc/ssl/certs/blabla"
        #altsubject_match="DNS:radius1.vse.cz;DNS:radius2.vse.cz"
        phase1="peaplabel=0"
        phase2="auth=MSCHAPV2"
	}
/etc/network/interfaces
> auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
	wpa-driver wext
	wpa-conf /etc/wpa_supplicant.conf

---

### Post by jarda-wien on 2007-05-13
bump

---

### Post by jarda-wien on 2007-05-13
bump

---

### Post by jarda-wien on 2007-05-14
bump

---

### Post by jarda-wien on 2007-05-15
what is wrong with this forum?

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

