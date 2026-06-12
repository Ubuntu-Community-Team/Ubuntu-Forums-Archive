---
title: "NAT error"
date: 2004-12-16
forum: Networking &amp; Wireless
---

### Post by erpe on 2004-12-16
I've read the post 'bout Azureus and the NAT error. I have the same problem and none of the solutions offered in that thread remedies that problem  :cry: 

I've got an alcatel speedtouch modem 510 with defaullt server on, works fine in XP (no low id at edonkey or problems with bittottent) In Ubuntu on the other hand i get NAT errors etc.  :confused: Can somebody help me to fix this problem?

---

### Post by p!=f on 2004-12-17
What's your network topography?
You have to allow some unprivileged port, 6881-6888 are suggested by default.
If you use shorewall add this rule to your /etc/shorewall/rules
> 
ACCEPT          net             fw              tcp     6881:6888

or if you have dedicated firewall and your client is behind it
> 
DNAT           net             loc:<ip>               tcp     6881:6888

where's <ip> is the IP address of the client you want to permitt bittorrent.
If you have any other firewall, post here which one.
If you have no firewall at all, check Azureus settings in the server tab.

---

### Post by erpe on 2004-12-17
You're reply pointed me in the right direction! I'v got Firestarter firewall tool installed,  but it wasn't running. I started Firestarter /rules dubbleclicked on open ports and entered 6881. Tadaa! Azareus vereified NAT setting ok  :grin:  Thanks for you're help!

---

### Post by JIuMnOnO165 on 2007-05-15
> **p!=f said:**
> What's your network topography?
You have to allow some unprivileged port, 6881-6888 are suggested by default.
If you use shorewall add this rule to your /etc/shorewall/rules

or if you have dedicated firewall and your client is behind it

where's &lt;ip&gt; is the IP address of the client you want to permitt bittorrent.
If you have any other firewall, post here which one.
If you have no firewall at all, check Azureus settings in the server tab.


[Equity Line Credit Tsunami Eminem pollution generator](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

