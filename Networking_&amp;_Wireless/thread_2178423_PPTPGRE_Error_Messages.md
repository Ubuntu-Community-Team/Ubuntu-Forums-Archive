---
title: "PPTP/GRE Error Messages"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by Elliot_Berg on 2013-10-03
So I've recently set up a PPTP server on my VPS, and it's working fine with numerous clients - however every time I connect I see an error in the logs, like below;

[FONT=arial]Oct  3 15:49:23 MACHINENAME pptpd[28940]: GRE: Bad checksum from pppd.

The connection is establish fine, and I can access the server with no issues once connected - so I'm not sure whether it's actually an issue or not. Can anyone shed some light on why it's happening, and how to stop it? I run OSSEC on this server (well, on all my servers) and so I'm getting this message emailed to me whenever I connect - and I'm loathe to add an ignore rule for it until I know it's not actually an issue!

Thanks![/FONT]

---

### Post by AtomicPenguin on 2013-10-03
This won't give you an answer to your question but I also get the same message in the log on my server upon connection to the PPTP server.  I've done a bit of searching and haven't come up with much so far.  I'll keep an eye on this thread.

---

### Post by Elliot_Berg on 2013-10-08
Noone?

---

### Post by Lars Noodén on 2013-10-09
Depending on what your goals are, PPTP may not be of that much help.

[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

It certainly won't help with security, if that's what you're after.

---

### Post by Elliot_Berg on 2013-10-09
That makes for interesting reading, but for my purposes I think it's probably reasonably safe - it prevents a generic external attacker being able to attack services such as SSH without first compromising the VPN - even once on the VPN I only allow key based auth, though. The only other thing you can do on the VPN that you can't from outside is relay mail through that server's mail server. That said, I set up PPTP simply because it's quick, easy, and all my devices can handle it natively - so if you have another protocol in mind that fits the bill I'll happily give it a go!

---

### Post by Lars Noodén on 2013-10-09
SSL or IPsec are usually the way to go, both with encryption obviously, if you still want a VPN.  However, if a service can't handle being on the Internet then it probably shouldn't even be connected to the LAN.  Though I guess there are cases, like using public wi-fi, where using an encrypted proxy would be of use.

For my remote connections I usually use plain SSH.

---

### Post by SeijiSensei on 2013-10-09
I would never use PPTP unless I were forced to support a variety of Windows machines and cannot control the software they have installed.  I much prefer [OpenVPN]("http://openvpn.net/") with a strong crypto algorithm like Blowfish or AES256.  There are OpenVPN clients for Windows and Macs as well as Linux.

---

### Post by Elliot_Berg on 2013-10-09
Unfortunately I do need to support a variety of clients - linux at home, windows at work, and (most restricted) un-rooted android devices such as a phone and tablet. I appreciate PPTP isn't the best protocol but after spending some time looking it appeared to be the easiest to set up, and the only one that would work natively with all devices.

---

