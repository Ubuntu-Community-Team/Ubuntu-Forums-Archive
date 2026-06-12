---
title: "Is it possible to use &quot;xsupplicant&quot; with Gnome NetworkManager?"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by slimpinto on 2006-11-10
Following a couple of Threads trying to get LEAP to work on my Xubuntu (Edgy) with IPW2200 (Intel Pro a/b/g) mini-pci with no luck. Using GnomeNM, that only has PEAP (with the wpa_supplicant, I assume), isn't an option here, since we use LEAP. Is there a way to use the xsupplicant (appears to support LEAP) with GNM? If so, how does one set that configuration up? Thanks in advance...

---

### Post by wieman01 on 2006-11-10
I don't know about NetworkManager, but wpa-supplicant can do LEAP. I have a sample configuration here if you don't mind configuring the network manually: 

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

However, I cannot promise it works because I have not tried it out myself. It would be cool if you tried & let us know how you went... You don't need xsupplicant, wpa-supplicant does the job.

---

### Post by slimpinto on 2006-11-14
OK, I've tried to configure it using your linked Thread, but still am having trouble. Can you recommend the config needed to use the following settings?

Encryption: WPA/TKIP or WPA2/AES

Authentication: EAP-Fast or LEAP, with your domain Username/Password

ESSID is <hidden> and we're using DHCP, as well...

Thanks in advance.

---

### Post by wieman01 on 2006-11-15
Ok, 2 script... one for LEAP, one for EAP-Fast (ESSID hidden). By I have no means to test them myself. So your feedback would be great.

_**LEAP:**_
> auto **wlan0**
iface **wlan0** inet dhcp
wpa-driver **wext**
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 2[/COLOR]
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt EAP-WPA
wpa-eap LEAP
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
_Commment:_ Authentication is LEAP, encryption is either WPA1 or WPA2, ESSID broadcast turned off.

_**EAP-FAST:**_
> auto **wlan0**
iface **wlan0** inet dhcp
wpa-driver **wext**
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 2[/COLOR]
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt EAP-WPA
wpa-eap FAST
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
wpa-phase1 fast_provisioning=1
wpa-pac-file [COLOR="Red"]/path/to/eap-pac-file[/COLOR]
_Comment:_ Authentication is EAP-FAST, encryption is either WPA1 or WPA2, ESSID broadcast turned off.

As highlighted before, this is all theory, I have not tried this myself. So it'd be cool if you could try for us. There is a bit of background that you may need to understand what we are doing (unless you know already of course):

[http://en.wikipedia.org/wiki/Extensible_Authentication_Protocol#LEAP]("http://en.wikipedia.org/wiki/Extensible_Authentication_Protocol#LEAP")

Not sure what your right "wpa-driver" ("wext") and interfaces ("wlan0") is though.

---

### Post by slimpinto on 2006-11-29
wieman01...thanks for all your help, but I was unable to get it to work. I've switched to Fedora Core 6 (as the wireless almost works out of the box) as I have more local resources to aid me here (at work) with getting it working. 

Nothing against Ubuntu...but it shouldn't take a week to figure out how to setup a secure witeless connection! I can barely imagine the frustration of a complete Linux noob trying to set this up...It's no wonder why Linux as a Desktop solution is taking soooooooo long to be accepted! Too many changes (6 month dev cycles) i.e. adding new features and not focusing on getting the previous release completely working first...I guess I shouldn't voice this opinion in a tech thread, so I'll stop now.  <end rant>

---

### Post by wieman01 on 2006-11-29
No, it's ok to make those comments here. Frankly, I share the same opinion. Wireless security is still insufficiently adddressed, networking has some way to go. The existing tools that come with Ubuntu by default don't really support security protocols (WEP being an exception). So I understand your frustration, I am feeling the same way.

---

