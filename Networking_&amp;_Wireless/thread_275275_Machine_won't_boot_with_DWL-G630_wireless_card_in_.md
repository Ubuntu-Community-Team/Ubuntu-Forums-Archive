---
title: "Machine won't boot with DWL-G630 wireless card in place"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by Metz on 2006-10-11
I'm trying to get my DWL-G630 card working. I've followed the various how to's, hints, tips and general 'try this's recommened in the forums. Problem is, I can't even boot with the card in place. It gets as far as 'Configuring network interfaces' and then stops. 

I Ctrl-C that step and it carries on. If the card is in place, when I log on, the machine locks up. 

If I switch to another session and log is there, that works until I try to sudo, at which point that session crashes.

If I try to run cardctl, it locks up. 

Any clues about where to start looking ?

---

### Post by jd65pl on 2006-10-11
Are you using the nidiswrapper driver for your card? If you are I have had some trouble at boot and so have other people.

Add
```
alias wlan0 ndiswrapper
```

To:
/etc/modules.d/ndiswrapper

That fixed it for me.

---

### Post by tturrisi on 2006-10-11
Do NOT use ndiswrapper w/ the DWLG630!
It has an Atheros chipset and should use the Madwifi drivers.

---

### Post by Metz on 2006-10-11
I don't have a /etc/modules.d/, btw

---

### Post by Metz on 2006-10-11
tturrisi, Apparently, my dwl-g630 has an RALink chipset...it's the E2 revision.

---

### Post by jd65pl on 2006-10-11
Oh sorry its

/etc/modprobe.d/ndiswrapper

But if your not using the driver then it is unlikely to be your solution. Is your card on the [supported devices list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") on the ndiswrapper wiki?

---

