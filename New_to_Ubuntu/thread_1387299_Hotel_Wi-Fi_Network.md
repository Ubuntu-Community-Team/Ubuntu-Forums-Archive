---
title: "Hotel Wi-Fi Network"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by caffeinated blood on 2010-01-21
My PC is a XP/Ubuntu dual-boot and I'm currently at a hotel using the provided Wi-Fi connected via ethernet - my PC has no wireless card. Last night I noticed a computer on Places-Network: "JohnDoe's MacBook"(not the actual name). Properties showed it "Shares Windows Network-Local". Normally, only "Windows Network" is listed. When I use XP, the ZoneAlarm firewall alert log will list those on the network in the building. But the one last night on Ubuntu had an IP address that was not in the building. Today the listing is gone. Does this sound like the same kind of listing that I normally see when I use XP? And why hasn't Ubuntu shown this before(been using the Wi-Fi long enough to know)? Finally, I"ve read that hotel Wi-Fi is not that secure. Is there anything I should do to make my Ubuntu more secure using this Wi-Fi?

---

### Post by steveneddy on 2010-01-21
Wi-Fi is wireless.

Ethernet connection is not considered Wi-Fi.

---

### Post by mikewhatever on 2010-01-21
You lost me on the first one - ZoneAlarm, XP and IP listing. Is there ZoneAlarm for Ubuntu? Where is the listing you were talking about?
As for security, many hotel WiFis are not encrypted, and hence not secure, but it has nothing to do with Ubuntu. You can make your data more secure and browsing more private by using https when browsing sites that support it, or a vpn service like swissvpn.net or itshidden.com.

---

### Post by 3rdalbum on 2010-01-21
Any unencrypted (non-password-protected) wifi is a security issue because everything is sent in-the-clear.

You say that you've plugged in via Ethernet, which means that you don't have this problem (because your data is not travelling through the air).

Ubuntu does not listen to incoming connections by default, so you are safe in this scenario. However, Macintoshes do not have such a stringent security policy and they will listen to incoming connections and broadcast their user's name over public networks. This is a potential problem for the Mac's user, but not for you.

In short, unless you're running some kind of server software, you are safe on this network when you use the Ethernet port.

---

### Post by caffeinated blood on 2010-01-22
Sorry for all the confusion. As you can probably figure, I'm still a new to Ubuntu. Let me try and explain again. My ethernet connection is off the room's wireless router/bridge which, of course, is wireless. The Zone Alarm firewall is on my Windows XP(dual-boot). I mentioned it because it will log the other users(guests) and their in-building IP addresses. The issue I've had is - while using Ubuntu I found a computer with an out-of-building IP address listed on Places>Network. I have always only seen Windows Network listed there. This new listing was shown as sharing the windows network-local. Since finding this listing last night it has now disappeared. What exactly was this listing and why did Ubuntu show only this one?

---

### Post by Scunnered on 2010-01-22
Like you I use a wifi connection in hotels and what I find is that in the wireless network connection details I can now see the hotels connection. Recently I went to the mainland to another hotel and on opening up the system found that there was a reference to the previous hotels connection on my system.  After connecting to the new hotels connection the next day the island hotel was not shown.

It appears that initially the system will display an old wifi connection just like a history of a web connection but that history disappears when away from that wifi.  I find that when I arrive home my first connection shows up the last hotel where I connected but that only lasts as long as my next shutdown.

I suspect what you saw was similar to my experience. As others have stated care should be taken when using the web over unsecured networks.

I hope this assists and re-assures you.

---

### Post by 3rdalbum on 2010-01-22
> **caffeinated blood said:**
> Sorry for all the confusion. As you can probably figure, I'm still a new to Ubuntu. Let me try and explain again. My ethernet connection is off the room's wireless router/bridge which, of course, is wireless. The Zone Alarm firewall is on my Windows XP(dual-boot). I mentioned it because it will log the other users(guests) and their in-building IP addresses. The issue I've had is - while using Ubuntu I found a computer with an out-of-building IP address listed on Places>Network. I have always only seen Windows Network listed there. This new listing was shown as sharing the windows network-local. Since finding this listing last night it has now disappeared. What exactly was this listing and why did Ubuntu show only this one?

I wouldn't worry about this. When you went to "Network", your system sent out a "broadcast" to the network, asking for any available shares. The Macintosh responded. I don't know why it's not from that particular network, but it's not anything to be concerned about because all your ports should be closed anyway.

---

### Post by caffeinated blood on 2010-01-22
But then why don't I see any other computers ever listed on "Network"? I went through the system logs and kept seeing avahi-daemon. After some Googling I found that avahi should be diabled for a hotel wi-fi if not needed. Could this have had anything to do with this other computer appearing on "Network"?

---

### Post by studmf on 2010-01-22
Ethernet is by no means "safer" to use on a public network.  I highly recommend using a VPN, there is a free one out there (Anchor, I think)  There are others such as hotspot...just do a search.

---

