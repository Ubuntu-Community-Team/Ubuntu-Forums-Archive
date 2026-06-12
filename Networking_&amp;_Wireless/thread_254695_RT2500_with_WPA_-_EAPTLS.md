---
title: "RT2500 with WPA - EAP/TLS"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by _Q_ on 2006-09-10
I searched the net for sometime now, and just didn't seem to find a working solution for me... :-| :-k 

I'm using the latest Ubuntu Dapper 6.06, which comes with built-in RT2500 wireless chipset support...

but, on the Administration -> Networking gui, there's just support for WEP...

there is also a offical ubuntu HowToRT2500 WPA, but it explains only the method of WPA-PSK which i don't use... :/

any ideas for a solution? .. thnx

(p.s. it seems that wpa supplicant, which is mentioned everywhere, doesn't support the RT2500 chipset.. :-? )

---

### Post by wieman01 on 2006-09-10
WPA_Supplicant should support RT2500 as well as far as I know. When you download the wpa_supplicant package, read the README file. There are examples of how so set up an EAP secured network. But here are the links for you (you find wpa_supplicant in the repositories:

General information:
[http://hostap.epitest.fi/wpa_supplicant/]("http://hostap.epitest.fi/wpa_supplicant/")

Examples:
[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/examples/wpa2-eap-ccmp.conf?rev=HEAD&content-type=text/plain]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/examples/wpa2-eap-ccmp.conf?rev=HEAD&content-type=text/plain")
[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain")

I am using WPA2 with PSK. If you are interested, this is the way I set it up (I am a bit paranoid):
[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

---

### Post by bryanl on 2006-09-10
Last I heard the RT2500 driver didn't have the hooks needed by the WPA supplicant. Has this changed?

---

### Post by danburney999 on 2006-09-12
I have wpa working with rt2500. But it will not connect at startup.

See: [http://www.ubuntuforums.org/showthread.php?t=256040&highlight=rt2500+wpa](http://www.ubuntuforums.org/showthread.php?t=256040&highlight=rt2500+wpa)

---

### Post by wieman01 on 2006-09-12
It connects at startup if you restart your network immediately during startup. That's what I did using a second "startup script"... works fine this way and I won't even notice I have to "up" it twice:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

It's a workaround but it save me restarting my network after I have logged on to the system.

---

