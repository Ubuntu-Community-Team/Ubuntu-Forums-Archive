---
title: "wpa_supplicant and Belkin F5D7010 PCMCIA adaptor"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by scarymonkey on 2005-04-10
Hi

I'm new to Linux but have managed to get my Belkin F5D7010 wireless adaptor (Broadcom based) working with wpa_supplicant. I have even managed to Ubuntu to load wpa_supplicant on boot which is something I have not managed on any other Linux distro I have tried (Lindows Five-O and Xandros 3.01OCE). My only problem is that I need to boot into Ubuntu and then physically remove the PCMCIA card for 15 seconds or more then push it back in before I get WPA to authorise correctly with my Negear DG834G router.

My current wpa_supplicant config file is
> 
ctrl_interface=/var/run/wpa_supplicant

ctrl_interface_group=0

eapol_version=1

ap_scan=1

fast_reauth=1

network={
	ssid="essid"
	psk="passphrase"
	priority=5
}


my etc/default/wpa_supplicant file to auto-enable wpa_supplicant is
> 
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless Driver
#  -i <ifname>		Interface (required, unless specified in config)
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

OPTIONS="-Bw -c/path/to/wpa_supplicant.conf -iwlan0 -Dndiswrapper"


Does anyone have any idea what could cause the adaptor not to come up correctly? If it helps when my system is setup for WEP encryption it is enabled and working on boot.

Regards

Vince Marsters

---

