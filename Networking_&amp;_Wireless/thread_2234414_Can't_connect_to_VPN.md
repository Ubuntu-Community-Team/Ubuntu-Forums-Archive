---
title: "Can't connect to VPN"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by ts1971 on 2014-07-14
Hi,

I am a pretty new Ubuntu (ver 12.04 LTS) user and I'm having trouble connecting to a VPN service I recently subscribed to.  I have two machines, one running Ubuntu and the other Windows 7 and both are behind a linksys router and a cable modem.  I was able to download the VPN service's proprietary windows software and everything work's fine.  

On ubuntu I was hoping to just connect manually using openvpn and towards that end I installed openvpn and downloaded both the UDP and TCP versions of the appropriate opvn file from the VPN service's website.  Then I su'd to root and issues this command:

```

openvpn --config fileNameOfOVPNFile

```

I am then prompted for my username / password which I enter and then there are a bunch of diagnostics spit out the screen, most of which mean nothing to me, but I don't see any that seem to indicate obvious errors.  The final line that's output is 'Initialization Sequence Completed'  So this all seems good, but then when I try to connect to webpage from my browser, everything just times out.  In order to restore internet connectivity, I have to CTRL-X in the XTERM where I started openvpn.  

I am new to both VPNs and Linux and I'm hoping that there is just some service I need to restart or something after I've connected to to my VPN service.  If that's not the case, can someone give me some pointers about how to troubleshoot this?

Thanks in advance!

---

### Post by mooreted on 2014-07-14
What VPN service is it? I can help you with Private Internet Access.

---

### Post by sammiev on 2014-07-14
+1 What VPN service is it?

---

