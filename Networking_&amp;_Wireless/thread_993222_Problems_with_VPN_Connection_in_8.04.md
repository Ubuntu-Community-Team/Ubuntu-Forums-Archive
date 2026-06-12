---
title: "Problems with VPN Connection in 8.04"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by turboswede on 2008-11-25
Hi, my girlfriend just got a Dell Inspiron 1525 with Ubuntu 8.04 installed. Our university uses vpn for internet, and allow people to use linux on it, but refuse to provide IT advice.

It seems that Hardy doesn't support vpn by default, so our plan was to use a wireless or normal connection at a friends flat to download the vpnc plugin for network manager. At an internet cafe, hardy seemed to be trying to roam and connect, but failed, and at a friends house, my girlfriend got it connected to a direct connection, could browse the internet, yet the add/remove programs(synaptic) program would not update its list and displayed an error message. We are going to try at someone else's house this weekend, and hopefully get the software downloaded.

Is there any reason synaptic would be playing up like that? I really should have written the error message down. Also, would it be easiest to upgrade to 8.10 now (i'll just download and burn the iso off my pc now)or later, and will it make the connections any easier? I heard that 8.10 has better wireless, but i havent read anything about vpn. 

Any quicker way to get it connected, are there any vpn options ive missed?

I'm in the process of moving my current windows xp laptop over to ubuntu, so this is a solution im going to need sometime down the line too.

Many thanks, Johan

---

### Post by turboswede on 2008-11-28
Currently at friends flat on a wired connection. Yet again, the laptop recognised a wireless network, yet would not connect to it. 

Currently upgrading to 8.10, hoping to have some better luck with the wireless then.

Will download the vpnc plugin after that, and then see how it goes.

---

### Post by turboswede on 2008-11-29
Ok, update to 8.10 went ok. It had a few hiccups with open office updates, but seemed to download and fix them again after a restart. And strangely enough, 8.10 automatically connected to wireless without a hitch, whereas 8.04 simply couldn't?

Will try to set up the vpn tonight, pretty sure it will work, so i will probably be marking this as solved then.

---

### Post by turboswede on 2008-12-11
Ok, took us a while to go to a wifi spot so we could download the PPTP extension for the network manager. But low and behold, I can't seem to work out what the vpn manager is asking me for. The terminology is almost completely different from that on windows.


here is an example of what I have managed to put in so far, if anyone could atleast tell me what the terminology translates as between windows and linux, that'd be great. I'm really just looking to copy what I see on my Girlfiends XP laptop to the Ubuntu, but its just not that simple:

```
UBUNTU        /    WINDOWS

Gateway       -    ?
Username      -    ok
Password      -    ok
NT Domain     -    ?
---------------------
AUTHENTICATION

PAP                ?  (Ignore these, I         )
CHAP               ?  (think the MS vpn is only)
MSCHAP             ?  (using mschap v2         )
MSCHAP V2     -    ok (MS vpn setting show this is used)
---------------------
SECURITY & COMPRESSION

MPPE-128      -    OK (MS vpn setting show this is used)

Echo- PPP     -    ?
---------------------
IPv4

DNS Severs    -    OK
Search Domains-    ?
DHCP Client ID-    ? Is this just the client IP?
---------------------
ROUTES
address/network/gateway - ?
```

And then I can't find where to put the proxy settings? or do I simply put that in firefox later?

I'm fine with computers in general, and have been reading up on linux for ages, but VPNs on  any OS, completely baffle me.

Any help would be great, it has been 77 views now, and not a single reply! 

Thanks, Johan.

---

### Post by turboswede on 2008-12-13
Ok, so the proxy settings are kept in a seperate client in the systems menu. got that.

The IT guys were able to shed some light on some basic settings, but I still can't get it to work.

I have disabled pap, chap, mschap, enabled mschap v2, mppe 18 bit encryption. 

There seems to be many bugs in 0.7 network manager however, I swear it never saves the mppe settings i put in. All the fixes and bug reports ive read for this really go over my head, and I have no knowledge on how to fix this.

I tried installing pptpconfig instead, with this guide: [http://www.ubuntugeek.com/how-to-install-pptp-gui-to-connect-windows-vpn-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-pptp-gui-to-connect-windows-vpn-in-ubuntu.html")
But this failed due to dependency issues, of gtk and glade files?

My girlfriend needs this computer for coursework, and without the network, it is pretty useless. Without any solution, I hate to say it, but we're just gonna install M$ Windows XP on it, as that atleast connects to a VPN.

This thread has now had 93 views. If you can't help, thats fine, but if anyone could atleast reply, or point me to a forum where I'll get more help?

Cheers.

---

### Post by turboswede on 2009-01-24
Ok, months and months later, we are both running ubuntu 8.10 on our laptops, and IT services on campus solved the problem.

I'm going to assume VPN is just a topic no one here wants to touch with a 50 foot pole, as I recieved a really prompt reply in my other thread about touchpads and synaptics.

SOLVED.

---

