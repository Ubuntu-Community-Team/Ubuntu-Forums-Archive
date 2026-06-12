---
title: "Problem SSHing to external hosts"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by 12__monkeys on 2007-11-01
I have recently installed Gutsy on a desktop and have installed SSH.  When completed I tested this from a Windows laptop and had no problems connecting.

The strange problem is that I can not connect to SSh servers external to my home network.  

Initially linking this to my router, I was found that I was able to connect to the same SSH server from my Windows laptop.

Is there something that I can check on my Gutsy desktop that would show what the problem could be?

Thanks

---

### Post by bingoUV on 2007-11-01
```

traceroute <server name>

```

This should show the various hosts your data passes through in its journey to the server named <server name>.  Do the same on windows laptop (I think it is called tracert in windows). See what is stopping linux from reaching the destination.

---

### Post by 12__monkeys on 2007-11-06
Thanks for the note, using traceroute I've what I think to be the root problem where network connectivity can be established using RJ45 network lead but *'not'* using my wireless LAN card.

---

