---
title: "USB Extension for USB wireless adapter KILLS all network interfaces"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by JasonSpradlin82 on 2008-08-09
I just received a USB 2.0 extension cable in the mail... If i plug it in and put the wireless adapter on it while the computer is running, the adapter doesn't seem to turn on.

If I do it after shutdown and start the computer back up, the computer not only doesn't see my ra0 adapter, but doesn't have the eth0 wired (pci) adapter either.  I restarted twice and both times only the loopback was listed in network tools and ifconfig and iwlist. 

I removed it and restarted again, and everything came back.

I'd like to USE the USB cable so that I can get better reception... Any idea what is going on?

---

### Post by JasonSpradlin82 on 2008-08-09
Not sure if it matters, but USB wireless adapter is connected to a 6-inch extension already... I simply added to that a 12-foot adapter... will having two extension cords cause problems??

---

### Post by JasonSpradlin82 on 2008-08-09
Well... just to update anybody having this problem, I seem to have figured it out... The USB 2.0 cable that I received in the mail today seems to be DOA.  I don't see any physical defects in it (cuts, tears, breaks, etc) but NOTHING that is plugged into it works. 

I assume that there is a short in it, causing it to mess with other devices on discovery.  

I found a way to get the computer to rediscover the USB wireless without rebooting as well.  As I mentioned, if I unplug it while the computer is on, ra0 disappears from my list of devices... When I plug it back in, I can't simply do sudo ifup ra0, because the computer has already "installed" it and says it is already up... i can't do iwlist or ifconfig because it doesn't recognize an ra0 network device.

I found, to my gladness, that if you run dhclient ra0, it actually goes and finds something like /LFP/ra0 (or something to that affect) instead of looking for an already defined ra0...

So, what i have to do, is run sudo dhclient ra0, and the first time it won't work, but now the computer recognizes it as a network device... After that I reassign my hidden SSID by typing "sudo iwpriv ra0 set SSID=Spradlin" and then i can immediately run "sudo dhclient ra0" to have it connect immediately

---

