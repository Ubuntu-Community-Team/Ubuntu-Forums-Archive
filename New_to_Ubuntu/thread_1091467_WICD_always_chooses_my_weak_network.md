---
title: "WICD always chooses my weak network"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by ronaldrand on 2009-03-09
Hello, I have a Linksys range extender. For some reason, wicd always chooses the weak network in the basement. I don't even have that network enabled in wicd. (But the router and the extender have the same SSID.) I would like if wicd would always connect to the extender because it has the best signal. (100% instead of 20%.) Any idea how to accomplish this in wicd?

Thanks.

---

### Post by imdano on 2009-03-09
Wicd doesn't actually try to connect to the weak network.  If you enabled debugging and checked wicd's log I think you'd see that it uses the correct bssid.  Are you using encryption?  My guess is wpa_supplicant (which wicd launches to authenticate) ends up choosing the wrong network to associate with because it shares its essid with the one you really want.  There may be something that can be tweaked in the wpa_supplicant template file or possibly in wicd itself to work around this.  I'll investigate and get back to you.

---

### Post by ronaldrand on 2009-03-09
> **imdano said:**
> Wicd doesn't actually try to connect to the weak network.  If you enabled debugging and checked wicd's log I think you'd see that it uses the correct bssid.  Are you using encryption?  My guess is wpa_supplicant (which wicd launches to authenticate) ends up choosing the wrong network to associate with because it shares its essid with the one you really want.  There may be something that can be tweaked in the wpa_supplicant template file or possibly in wicd itself to work around this.  I'll investigate and get back to you.

I looked in the logs. I didn't see anything, except that it was trying to connect to the Mac address of the range extender. I don't know why it chose to connect to the router which has about an 80% lower signal and that access point isn't even enabled in wicd. Sounds like a bug to me. (Not that every other network manager doesn't do the same thing, but the way wicd is set up, it seems like the way it should work.) What is the point of the Range Extender if I can't connect to it? ALso, I like to be connected to it in case it stops working so I can fix it before anyone else in the house notices. I'd appreciate if you could figure something out like you said.

---

### Post by imdano on 2009-03-11
> **ronaldrand said:**
> I looked in the logs. I didn't see anything, except that it was trying to connect to the Mac address of the range extender. I don't know why it chose to connect to the router which has about an 80% lower signal and that access point isn't even enabled in wicd. Sounds like a bug to me. (Not that every other network manager doesn't do the same thing, but the way wicd is set up, it seems like the way it should work.) What is the point of the Range Extender if I can't connect to it? ALso, I like to be connected to it in case it stops working so I can fix it before anyone else in the house notices. I'd appreciate if you could figure something out like you said.Are you using encryption?  Like I said, wicd isn't choosing to connect you to the router, it's using the MAC address of the range extender.  I think either wpa_supplicant (if you're using encryption) or your wireless driver (which wicd uses through iwconfig/ifconfig) is confusing the two APs.  Do they both share the same essid/channel?  Can you post the contents of /var/log/wicd/wicd.log?

---

