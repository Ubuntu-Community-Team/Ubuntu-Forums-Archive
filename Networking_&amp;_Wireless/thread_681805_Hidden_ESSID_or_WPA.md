---
title: "Hidden ESSID or WPA?"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by drfox on 2008-01-29
I have a wireless network that doesn't broadcast its ESSID. My notebook has an intel wlan card. I'm running gutsy 32
I've tried network manager, wifi-radar, and WICD, and none is able to connect to it if I set WEP or WPA security. 
A windows machine has no problem connecting.
My question: is my network more secure with a hidden ESSID or witha broadcast SSID with WPA security?
And when is this hidden network problem going to be fixed?

Larry

---

### Post by michaelzap on 2008-01-29
> **drfox said:**
> I have a wireless network that doesn't broadcast its ESSID. My notebook has an intel wlan card. I'm running gutsy 32
I've tried network manager, wifi-radar, and WICD, and none is able to connect to it if I set WEP or WPA security. 
A windows machine has no problem connecting.
My question: is my network more secure with a hidden ESSID or witha broadcast SSID with WPA security?
And when is this hidden network problem going to be fixed?

Larry

i don't think that not broadcasting your ESSID adds any real security at all. If there's traffic on your wireless network, kismet will pick it up and identify your router. So that's not worth doing if it complicates the use of encryption.

WEP can be cracked in a couple minutes or less. WPA is far more secure. Personally I would never use anything but WPA.

You could also restrict access to your network by MAC address, but unless you use WPA encryption I don't think that anything else that you do counts for diddly.

---

### Post by kegobeer on 2008-01-29
Since most anyone can detect and connect to hidden networks, there's really not much point in hiding the SSID.  It is not a security measure, so don't rely upon it to protect your network.  Use WPA2 whenever possible (don't use anything less than WPA).

The last I heard, the hidden SSID issue has been fixed in the NetworkManager package in Gnome but not in the Ubuntu network-manager package.  Here's (I believe) the original bug report for the hidden SSID problem; it's still open and will probably be a problem in Heron as well.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/39707](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/39707)

I believe there has been a patch released that claims to fix the problem, but I haven't tried it.  I just broadcast my SSID and use WPA2 with an AES cypher.

---

### Post by drfox on 2008-01-31
Thanks. I tried broadcasting my network, using WPA1 with an AES password combination of letters and numbers, and I can't connect using WICD, NM, or WiFi Radar. Back to the hidden network and back to the drawing board  :(

Larry

---

### Post by kevdog on 2008-01-31
Take a look at my post about connecting from the commandl line.  Im not saying this will be the everyday solution for you, but it will at least give you an indicator if WPA is possible.  What kind of wireless card do you have (lshw -C network), WPA1 is usually with TKIP and AES usually with WPA2 (but not in all cases).

---

