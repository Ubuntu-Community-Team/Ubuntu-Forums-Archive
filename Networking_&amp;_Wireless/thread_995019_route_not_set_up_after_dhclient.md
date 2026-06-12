---
title: "route not set up after dhclient?"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by nafur on 2008-11-27
Hello,

I have a notebook with Ubuntu intrepid...
wireless drivers are working, but i have problems with my routes.

I mainly use two different networks, one at home and one at university (both wpa2, at home personal with  psk, at university this enterprise stuff... called eduroam if anyone knows ist...)

I configured it via wpa_supplicant. When I connect, everything is fine (usually) and after some seconds, my device is "associated to ***" and "key negotiation completed". Then I run dhclient, and it works (device is bound to some ip I get from dhcp. before all this is started, I take eth0 (wired lan) down so that it can't do any harm...

At university, everything is fine now: I can access the internet and everything is routed correctly.
But at home, it fails... I assume that something is wrong with the routes, as "route" prints out the localhost-route but hangs than for about 2 or 3 minutes before it finally prints the correct route to the network. Anyway, I'm not able to ping anything, not even the IP of the router i got my ip from...
Sometimes it suddenly works, but that usually takes from 5 up to 30 minutes, sometimes it doesn't work at all for hours. But anyway, it stops working again after a few minutes.

my wpa_supplicant.conf looks like this:
```
network={
	ssid="eduroam"
	priority=11
	key_mgmt=WPA-EAP
	eap=TTLS
	phase2="auth=PAP"
	identity="*****"
	ca_cert="/etc/ssl/certs/eduroam-chain.pem"
	anonymous_identity="*****"
	password="*****"
}
network={
	ssid="*****"
	group=CCMP
	pairwise=CCMP
	key_mgmt=WPA-PSK
	#psk="*****"
        psk=*****
}
```

Does anyone has any idea why this happens? I'm running out of anything i can think of :(

---

