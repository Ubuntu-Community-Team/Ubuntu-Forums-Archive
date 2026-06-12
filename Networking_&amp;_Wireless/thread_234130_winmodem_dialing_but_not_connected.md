---
title: "winmodem dialing but not connected?"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by Sunnz on 2006-08-11
I have been following this guide: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Setting up my builtin modem on my laptop.

So far, it seems the drive worked, as I can hear it dialing and "talking" to the server.

But, what's up with this? (See picture.) It takes a long to to display that ppp0 is connected, yet it doesn't actually have access to the net. I tried to ping google as well - can't lookup host name or  something.

---

### Post by Sunnz on 2006-08-11
Just tried wvdial... did not work to begin work but now working when I enabled stupid mode... what's going on?

---

### Post by jplinux on 2006-08-11
have a look on the route used ...
Set your route  manually as
/sbin/route add default  gw <ip_address_ppp0_interface>

It should work...

---

### Post by Sunnz on 2006-08-13
What is that for? wvdial works; but only ifunder "stupid mode".

Would that route thing make it so I can use the gnome widget thing to dial up?

---

### Post by towsonu2003 on 2006-12-05
> **Sunnz said:**
> only ifunder "stupid mode"

don't worry, that's fine. mine (and many others') work the same way. here's what its documentation mentions:
[quote=http://www.die.net/doc/linux/man/man5/wvdial.conf.5.html]
Stupid Mode
    When wvdial is in Stupid Mode, it does not attempt to interpret any prompts from the terminal server. It starts pppd immediately after the modem connects. Apparently there are ISP's that actually give you a login prompt, but work only if you start PPP, rather than logging in. Go figure. Stupid Mode is (naturally) disabled by default.[/quote]

---

