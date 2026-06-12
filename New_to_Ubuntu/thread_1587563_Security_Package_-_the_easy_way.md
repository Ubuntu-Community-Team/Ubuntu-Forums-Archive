---
title: "Security Package - the easy way"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Aetixintro on 2010-10-03
Caution: this is not meant as an alternative to the most serious advise on security. This only represents a few good and very effective ways to have a trouble-free computer system by Ubuntu.

Programs:
iptables (also ip6tables if you want to)
Firestarter
iptstate
AppArmor
Network Tools (from here, you can also report abuse by using whois-service)

Rules for the iptables by Firestarter
INBOUND - allow services for your email **by your email account**
You can also allow your local address, ie. 0.0.0.0 or 127.0.0.1 or some.
DENY everything else (drop silently) - deny is included automatically by the non-listing.
You know, on INCOMING, feel free to block everything that shows up on events except local (0.0.0.0 and 127.0.01) and your own IP address.

OUTBOUND - allow for all the services you want - http, https, smtp, ftp and the rest.
For these services, make sure you make them from firewall host, yourself.
Allow **no** connections to yourself (host) also automatically included.
This is the restrictive by default, whitelisting traffic.

(It's a premise that all the programs involved are flawless.)

I'll look for improvements to this post, but this is the simplest and by that, the best. Almost no understanding required, just to go at it.

Enjoy computing! Cheers! :D

---

### Post by andrewthomas on 2010-10-04
Not the best idea.

> Firestarter is an application for configuring your Ubuntu (GNU/Linux)  firewall. It was formerly very widespread, **though it is no longer being  actively maintained or developed, and thus cannot be guaranteed to be  fully secure**.
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by sikander3786 on 2010-10-04
> **andrewthomas said:**
> Not the best idea.


[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)
+1 here too.

Unless firestarter's development starts again, there will be too many security glitches in it, showing up day by day and you can't feel that much secure then.

iptables, ipstate and AppArmor can be used alongwith UFW.

---

### Post by Aetixintro on 2010-10-04
It says on its homepage, [http://www.fs-security.com/](http://www.fs-security.com/), that the manual has last been updated November 26, 2009. Though it also says that the website only has copyright to 2007, suggesting that it is passive, that development has ceased.

I wonder how complicated it is to develop as its only job is to update the Iptables and have the lockdown possibility. I guess one can download the code oneself and develop it or keep it backed up just in case.

You can also add Network Tools that come with Ubuntu as default, as a program to have running in a secondary desktop window, just in case.

---

### Post by bodhi.zazen on 2010-10-04
I would suggest you use ufw, gufw, or iptables directly.

```
sudo ufw enable
``` is sufficient for 99.99% of desktop users, no need for firestarter.

As there are no significant listening services by default, I am not convinced adding a firewall does all that much.

---

### Post by 3rdalbum on 2010-10-04
Especially when most people use a NAT router that functions as a firewall anyway.

---

### Post by Aetixintro on 2010-10-12
> Firestarter is an application for configuring your Ubuntu (GNU/Linux)  firewall. It was formerly very widespread, **though it is no longer being  actively maintained or developed, and thus cannot be guaranteed to be  fully secure**.From the Firestarter man-pages.

Although I can report that Firestarter has been given a new Reload Events button that is now silvery in the newest Ubuntu, Maverick Meerkat 10.10! So there you go! Firestarter is blinking through! (Alright, maybe Firestarter is set up with a default system reload button.)

Besides, you can do well with Firestarter by these commands toward IPtables:
```
sudo iptables-save > /etc/iptables.save
sudo iptables-apply /etc/iptables.save [Comment:]/* choose whatever filename you like as long as it's a iptables save-file. */
```Go Firestarter! Go Firestarter!

---

