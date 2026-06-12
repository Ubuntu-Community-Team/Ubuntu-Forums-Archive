---
title: "Trouble permanentely setting wireless up"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Klinkaroo on 2008-04-29
Ok here is the problem. I can get my wireless card to work no problem but I have to use the terminal to tell the computer what the WEP key is.

What I do is.

```
sudo iwconfig ath0 key *key goes here*
```

then
```

sudo dhclient ath0
```

when I do this in the terminal I can get my internet to work just fine, problem is it doesn't stay and every time I reboot I have to retype everything, would love to be able to set it up so I wouldn't have to.

Any suggestions?

I tried using the network management tool, I typed in the SSID, and the wep key with the WEP (ACSI) encryption setting and the ip set to get it by DHCP and still can't get it to work, only been able to get it to work though the terminal.

---

