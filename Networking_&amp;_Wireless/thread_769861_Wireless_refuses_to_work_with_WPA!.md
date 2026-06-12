---
title: "Wireless refuses to work with WPA!"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by ShadowGray on 2008-04-26
Okay, so I have a Netgear WG111v2 USB wireless adapter for one of my desktops, and I recently installed ubuntu on it.  I did the ndiswrapper method for the Dell 1390 except I changed around driver names and blacklisted rtl8187.

It sorta works, it can see networks and connect, but whenever I try to connect to my network with a WPA key, it doesn't connect and sends me the key prompt window a second time.  I know I put in the key correctly.  However, if I turn off the WPA security, it connects fine.

I don't want to run a network without security.  I have temporarily limited access by MAC address, but I know that's not as secure as having an actual WPA encryption.

Is there a fix for this, or is this just one of the limitations of using Ubuntu/ndiswrapper?

---

### Post by ShadowGray on 2008-04-26
Anyone?  I'm running a WG111v2 adapter and a WGR614v6 router.

---

### Post by kevdog on 2008-04-27
Does the driver you are using with ndiswrapper support wpa?  Either a search when typing dmesg (please dont post the entire results here) or a search on the internet regarding the driver may help you discover if wpa is supported.  If it is, I when then try to configure the wpa connection manually since it will provide you other debugging messages to hopefully fix your problem.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by ShadowGray on 2008-04-27
The driver should work, since on windows it worked fine, so it's not a new adapter.

I'll try the above instructions later tonight.

What other problems could it be?  maybe it's the default settings when using the built in wireless interface?

---

### Post by sennep on 2008-04-27
I managed to get the wg111v2 working in 7.10 with WPA using the ndiswrapper method, but it doesn't seem to work for me in 8.04, so there must be someting different with Hardy. I'll try to troubleshoot when I get the time and post the results if it's any help to you Shadowgray. Note that there is a trick to finding the right driver with this adapter though, it won't necessarily work with the driver on your netgear CD even though it works with windows. I had to download a different driver to get it working. See the link in my signature for links to drivers if you want to try.

---

### Post by ShadowGray on 2008-04-27
Well, it's running, but it won't access WPA... which is what confuses me.  It works fine when I set my router to unsecured though.

Right now I've hidden the SSID and limited access by MAc addresses... but I just want to have regular WPA working.

---

### Post by kevdog on 2008-04-27
So did you try to connect manually with the WPA connection?

---

### Post by drw777 on 2008-04-28
I'm having the same problem using a Dell 1390 with NDISwrapper 1.52.  I can connect to an unsecured network we have in the office but I cannot get on the WAP.

---

### Post by infarct on 2008-04-29
Hi,

I have been having a similar problem. I have only been using linux for a few weeks now so am still on a steep learning curve.

I have an acer 5315 laptop with the infamous atheros wireless. Under 7.1 I was able to get it to work (using ndiswrapper ..). Since upgrading to 8.4 I am unable to use any wireless encryption.
I am thinking of going back to 7.1...

---

### Post by quebecois on 2008-04-30
> **ShadowGray said:**
> Anyone?  I'm running a WG111v2 adapter and a WGR614v6 router.
How your router is configured? 

I had a similar problem with my marvell 8335 based wifi card, and my DI-624 router.. Wifi on DI-624 was configured WPA-PSK TKIP.  When I switch to WPA-PSK AES, it works...

Which cipher is configured on you router? TKIP or AES?  If it's TKIP, try AES, if possible.

---

### Post by infarct on 2008-04-30
Hi,

As a follow up from my previous post, I have now got WPA working.....

I ended up reinstalling 8.4, installed ndiswrapper and used the atheros driver that I got from their website.

It now seems to work fine (I have an acer 5315 with atheros wireless).

It is now week 3 since I said good bye to window$!!!

:guitar:

---

### Post by kevdog on 2008-04-30
Yes others have reported problems with TKIP and Hardy.  I don't know why but the solution was AES -- you want AES anyway since its a more efficient cipher than TKIP -- so its not really a loss.

---

