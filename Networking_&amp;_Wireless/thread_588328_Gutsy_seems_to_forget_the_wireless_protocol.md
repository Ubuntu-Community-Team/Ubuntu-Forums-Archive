---
title: "Gutsy seems to forget the wireless protocol"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by dmz17 on 2007-10-23
Setting up Network Connections to my access point, I specify WPA2 Personal and my passphrase. It works.

Booting the machine, no network. I go back into Network Settings, look at the settings for the card, the password type field now says 'WPA Personal', ie not 'WPA2 Personal'.

I have found a workaround to  get rid of the need for the GUI:

Upon boot run a script as root:

/etc/nit.d/networking restart

This works immediately, but seems unnecessary. Since I dual boot with SuSE, at wireless does not work on SuSE when ESSID is not broadcast, I now do broadcast the ESSID.

---

### Post by pparks1 on 2008-02-03
I've having exactly the same issue.

I have a Dell Latitude D610 laptop with a Broadcom based card.   I installed Gutsy, it asked about the restricted firmware driver on boot up.  I said yes, installed the driver, configured my WPA2 settings and it just worked.

However, after rebooting, it doesn't work.  If I go into the Network utility, it says WPA for the protocol.  However, if I simply issue sudo /etc/init.d/networking restart...it comes up and everything works properly.

Anybody with any suggestions on fixing this, or simply issuing in an rc.local style file at the end of the bootup?

---

### Post by mike.headon on 2008-03-07
Yeah - me too! :)

But - in my case I can add that it happened when I changed my router from WEP to WPA. When I was on WEP everything worked perfectly first time. So, I said to myself, time to tighten my security - what could go wrong:confused:

---

