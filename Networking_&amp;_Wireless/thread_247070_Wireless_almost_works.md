---
title: "Wireless almost works"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by postmessages on 2006-08-30
Hi,
I have a D-Link DWL-G122 (rev. B1) USB wireless adaptor. After I first installed Dapper and tried to use the adaptor, the system froze. I've overcome the system freeze (using ndiswrapper) and have now got wpa_supplicant, which is supposed to be the method of using WPA-PSK in Ubuntu.

Anyway, when I try to use wpa_supplicant to connect, the lights on the adaptor come on (up to this point, it hadn't done this) but it gave me an error message saying that the 4-way handshake had failed, possibly due to the psk being incorrect. Clearly this isn't the problem, so what is?

Any ideas?

---

### Post by funchords on 2006-08-30
I'm inclined to believe the error.  Usually, any other failure would not have allowed it to get as far as the 4-way handshake.  

Let's clear out any bad lockouts.  Reboot the computer and, as it's rebooting, power down/power up the Access Point.  Try again.

Other things...


Check your wpa_supplicant.conf for use of the quotes when a space is involved:

network={
	ssid="myssid"
	scan_ssid=1
	psk="very secret passphrase"
}

or 

network={
	ssid="myssid"
	scan_ssid=1
	psk=06b4be19da289f475aa46a33cb793029d4ab3db7a23ee92382eb0106c72ac7bb
}

Another thing that might cause a 4-way handshake to fail would be nonsensical timing parameters.  But if you have not specified any timing parameters in wpa_supplicant.conf, then this won't be your problem.

---

### Post by libertyforever on 2006-08-31
Don't know if this will help, but you may want to check out [THIS]("http://www.ubuntuforums.org/showthread.php?t=190703&highlight=dwl-g122+b1") thread. I was having similar problems and that thread fixed it for me. Though the thread is for a D-Link G120 and I have a G122 like you, it worked for me. Read all the way down to Sam Lui's and my posts. Hope it helps.

---

