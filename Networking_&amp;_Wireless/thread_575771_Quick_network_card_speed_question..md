---
title: "Quick network card speed question."
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by thor111 on 2007-10-14
Hopefully there's a quick answer!  I've got a 100 MB card that I want to force to run at 10 MB because the cable run in my house doesn't support 100 MB.  I know this is a problem, because I've seen it with windows, and the fix is VERY easy in windows.  Unfortunately, I don't see any option to force the connection speed to 10 MB/s with Ubuntu.  Hopefully, I've missed something, and it's a simple fix.  Thanks for any help.

-Mark

---

### Post by ddrichardson on 2007-10-14
If the cable in your house doesn't support 100Mbs then you wont get 100Mbs - there is no need to restrict the speed the card operates at. If you insist though:```
sudo ethtool -s eth0 speed 10
```

---

### Post by thor111 on 2007-10-14
Thanks!  Setting the speed worked as I predicted.  I'm now responding through the network card that wasn't working 10 minutes ago.  The only thing else I had to do was to turn off the auto-negotiate.  Will it remember all the changes?

Thanks again!

-Mark

---

### Post by thor111 on 2007-10-24
It's been about a week, and I haven't heard back, so I thought I'd try changing the title, and reposting.  I'd like to make the following commands permanent - any ideas?

Sudo ethtool -s eth0 autoneg off
Sudo ethtool -s eth0 speed 10

I then have to disconnect and reconnect to get a legitimate connection.  Help please

Thanks,

-Mark

---

### Post by ddrichardson on 2007-10-25
Not totally sure about this, but I would have thought they could be added to /etc/modprobe.d/options, try:```
eth0 autoneg off
eth0 speed 10
```

---

### Post by thor111 on 2007-11-03
Thanks for the response.  That didn't appear to work.  I think that the /etc/network/interfaces file should be edited, but I'm not sure of the proper syntax.  Thanks again for trying.

-Mark

---

