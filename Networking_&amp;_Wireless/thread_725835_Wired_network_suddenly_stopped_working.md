---
title: "Wired network suddenly stopped working"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Azgard on 2008-03-16
So yesterday I was using Ubuntu fine on my laptop as always, I'm using 7.10, then I had to boot into XP to do a project, so did that. Then once I booted back into Ubuntu, the network was just dead, it had the correct IP set, but my ADSL wouldn't connect, it gave an error in PPPoE discovery I believe, and pinging other hosts in the network just didn't work, gave a host unreachable error.

I tried using another cable and another port on my router, but this didn't help at all. I initially thought the built in network card was giving problems, as it has done before in openSuse, but then I went back into Windows and the network is working fine.

Any ideas? I really need Ubuntu, and would hate to have to reinstall it.

---

### Post by jan quark on 2008-03-17
can you please post the results of these terminal commands:

```
iwconfig
sudo lshw -C network
cat /etc/netwrok/interfaces
```

---

### Post by Azgard on 2008-03-17
Sure I can do that later when I get home.

Isn't iwconfig for wireless interfaces? Or am I mistaken?

Also a friend of mine asked me to do "ip a l" which gave an output that contained NO CARRIER for my network card, apparantly thats a bad thing?

It does work randomly, sometimes when I reboot it works, sometimes not.

---

### Post by superprash2003 on 2008-03-17
yes iwconfig is for wireless interfaces

---

### Post by Iowan on 2008-03-17
Did you do a power-down reboot?  I've read that sometimes rebooting from windows doesn't get drivers reset (or something like that).
Also, a slight typo - should read:```
...
cat /etc/network/interfaces
```

---

### Post by Azgard on 2008-03-17
Hmm, from Ubuntu I tried rebooting and shutting down fully, i.e. poweroff, but that had no effect. I'm not too sure about from Windows though.. I think I've only rebooted from Windows, not actually powered down, will try it later.

Yea, I realised that was a typo ;)

---

### Post by Azgard on 2008-03-19
I've tested, and when I shutdown properly from Windows, then it works fine in Ubuntu, at least I know the cause now :)

---

