---
title: "Ubuntu 6.06 Wlan problems"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by Salwiak on 2006-12-22
I've just recently decided to give Ubuntu a try, after using only Windows for +10 years, so i'm a bit of a noob, so pardon me I don't understand you :P

My problem is my wlan. I'm using a Atheros AR5006X Wlancard ([http://www.atheros.com/pt/AR5006X.htm](http://www.atheros.com/pt/AR5006X.htm)) which connects to my Linksys WRT54G router. The wlancard seems to be supported in Ubuntu, as i find connections with the Networking tool (System > prefrences > networking)
The problem is, i can't seem to connect to my own wlan. The networking tool does not automatically fins the ESSID, but when i type it in, it seems find it. So I type in the WEP, and press ok. A loading screen pops up and says "Activating Interface ath0" and that's it. The screen dissapears, the interface is activated, but I can't connect to the intenet :confused:  (NOTE: I'm running Ubuntu from LiveCD) And it works flawlessly in Windows!

After looking for guides the whole day, i tried "sudo iwconfig" after activating the interface, and got this: 
```
ubuntu@ubuntu:-$ sudo iwconfig:

	lo: no wireless extensions

	eth0: no wireless extensions

	wifi0: no wireless extensions

	ath0: IEEE 802.11g ESSID:"sateenkaari"
	Mode: managed Channel:0 Access point: Not-associated
	Bit Rate: 0kb/s Tx-power: 13dBm Sensitivity=0/3
	Retry: off RTS thr: off Fragment thr: off 
	Encryption key: off Link Quality=0/94
	Signal level=95dBm Noise level=-95dBm
	Rx invalid crypt: 0 Rx invalid frag:0
	Tx sensitive retries:0 Invalid misc:0 missed beacon:0
	
	sit0: no wireless extensions
```

According to the guides, I should a code after "Access Point", xx: xx: xx: xx: xx.
Now why can't i see that? Is it the router, or something else? :-k 
How can I fix this? Or is this even the problem? I'm really quite confused


Any help is greatly appreciated! Merry Christmas and a happy new year to everybody! :)

---

