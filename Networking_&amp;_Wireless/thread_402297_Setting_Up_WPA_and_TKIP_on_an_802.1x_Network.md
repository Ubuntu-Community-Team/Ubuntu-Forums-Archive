---
title: "Setting Up WPA and TKIP on an 802.1x Network"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by aarmenaa on 2007-04-05
I am trying to connect to my school's wireless network.  They don't officially support Linux, but they do give me some information.  I have Xsupplicant 1.2.4, wpasupplicant 0.5.4, and my wireless card installed through ndiswrapper 1.18.  Ubuntu 6.10 (edgy).  I have read through many tutorials and none of them seem to address my particular setup.  I tried configuring on my own, but authentication always fails.  So, I'm hoping someone here can help me write a config file and start the supplicants correctly.

[QUOTE=School's Wireless Configuration Page]SSID: hornet
Authentication Method: 802.1x
Authentication Type: EAP-TTLS
Encryption Type: WPA
Key Style: TKIP
Certificate Authority: Thawte
Domain: (leave blank)[/QUOTE]
[LINK: My school's page describing how to set up networking on a Mac.]("http://www.spsu.edu/infotech/wireless/MacConfig.html")

---

### Post by davidgarcin on 2007-04-05
Here's a link to a page someone set up at my school - the situation is similar, so you should be able to follow it fairly closely.

[http://www.calvin.edu/%7Edjs32/ubuntu.html](http://www.calvin.edu/%7Edjs32/ubuntu.html)

If that doesn't work, let me know and I can post my config stuff (I've actually connected to a similar network in a different way).  I would post it now but I don't have access to my comp.

-Dave

---

### Post by aarmenaa on 2007-04-05
Hi, Network Manager was my first try, but it didn't seem to work.  Just in case, I went back and tried it again, but it's still a no-go.  I'm not entirely sure that Network Manager is starting wpasupplicant, and I can't see where it's writing any configuration files, so I have no idea if it even doing anything correctly.  So, I've been trying to write my own configs because of that.

---

### Post by aarmenaa on 2007-04-05
Just a quick update, I managed to get into the AUTHENTICATED state for the first time in the month or so I've been working on this!  However, it now endlessly restarts the process, going from RESTARTING to AUTHENTICATING to AUTHENTICATED.  This is, of course, kinda useless.  Also, I think Network Manager doesn't have any way of setting the authentication to occur inside PAP.

I used xsupplicant and this configuration:
```
network_list = default, hornet

logfile = /var/log/xsupplicant.log

default
{
}

hornet
{
	type = wireless
	wireless_control = yes
	allow_types = eap-ttls
	identity = anonymous

	eap-ttls
	{
		root_cert = /etc/ssl/certs/Thawte_Server_CA.pem
		phase2_type = pap
		pap
		{
			username = <omitted>
			password = "<omitted>"
		}
	}
}
```

---

### Post by davidgarcin on 2007-04-06
ok, to connect to my school's network I'm using wpa_supplicant, and nothing else.  I tried NetworkManager at one point, but I never got it to co-operate with wpa_supplicant, probably the same problem you had.

here's my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

auto eth0
iface eth0 inet dhcp
```

the entry for eth1 (the wireless connection) is the one of interest in this case.  The last line of that section is the wpa_supplicant config file:

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

# for home
network={
        ssid="linksys"

        key_mgmt=NONE
        wep_key0=myWEPKey
        wep_tx_keyidx=0
}

#for the folks' place
network={
        ssid="ssid"
        psk="ascii_wpa_key"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        auth_alg=OPEN
        priority=1
        disabled=0

}

# for airCalvin
network={
        ssid="airCalvin"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="username"
        password="password"
}
```

The entry for airCalvin is my school's wireless network.  Your's will differ somewhat, see the following link for extensive config examples:

[http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant/wpa_supplicant.conf](http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant/wpa_supplicant.conf)

I had to play around with the ap_scan variable at the top to get it work properly.  In the end, it was a lot of trial and error.

Hopefully that helps, even though my situation isn't exactly the same.

---

