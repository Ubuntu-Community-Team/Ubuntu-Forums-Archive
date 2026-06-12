---
title: "Atheros 5005G  Acer Aspire 5102WLMi"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by stmdk on 2007-02-01
During installation the wireless adapter was discovered but it could not pull an IP from DHCP of the router.  Therefore I skipped the wireless setup.  When I get into X and try to configure with the WLAN configuration I'm told that no adapter exists.

I'm still a bit of a novice with Linux so please explain how I can resolve this and get my wireless back up?

BTW the Acer Aspire 5102WLMi is very uncooperative with linux distros.  Kanotix wouldn't even boot.  Knoppix installed but was complete unstable and refused to boot back up on the second try.  Ubuntu found everything INCLUDING the sound.  The wireless seems to be the only snag.  Thanks ubuntu.

---

### Post by tturrisi on 2007-02-01
enable the multi-universe repos and install the restricted modeles for your kernel, it contains the madwifi drivers for atheros chipsets.

---

### Post by stmdk on 2007-02-01
Got it up and working with madwifi.  Had a bit of a problem with dhcp but worked it out.  Thanks!!!

---

