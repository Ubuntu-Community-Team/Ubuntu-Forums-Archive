---
title: "PPPOE Connection Setup."
date: 2010-07-20
forum: New to Ubuntu
---

### Post by khushalb on 2010-07-20
Well I just had recently setup the pppoe connection using sudo pppoeconf command and the internet had worked for me. But once I restarted my comp it again didnt work so seeing help file i used the "pon dsl-provider" command to switch it back on but it seems that now the internet is not working.

I again used the pppoeconf command but now I cannot even configure it back again coz it isnt detecting a connection. It appears that My network card is disabled.

Any solution guys?

---

### Post by dineshs on 2010-07-20
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by khushalb on 2010-07-20
Well it worked Dinesh Thank you so much. DSL connection 1 is created and can be connected.

But there's another issue with the Wired Connection Auth etho keeps popping up. I check the properties and it says connect automatically. When I remove that checkbox option. Its asks me for my admin password which when i add it does not authenticate and it stays on that screen.

Any solution for that? Also Dinesh let me know your gmail email id so that I can add to my friends list. Just PM me your email Id.

---

### Post by khushalb on 2010-07-20
Also will I always have to make a DSL connection going into System and network manager. Aint there a way where I can download PPPOE DIALER. I had read your thread where u referred to installing a package gpppo. But I think this is no longer available.

---

### Post by dineshs on 2010-07-21
> Also will I always have to make a DSL connection going into System and network manager
No
> Aint there a way where I can download PPPOE DIALER
When you want to connect DSL click on the NM icon then click DSL connection1 as in the attachment
> I had read your thread where u referred to installing a package [COLOR="DarkRed"]gpppo[/COLOR]. But I think this is no longer available. 
It is gpppon. But it is required only if you are connecting DSL using pon/poff.Since you are using NM do not try pppoeconf command or pon/poff.So forget gpppon

---

### Post by dineshs on 2010-07-21
here is the attachment

---

### Post by khushalb on 2010-07-24
Whats the wvdial application. Can that thing work?

---

### Post by dineshs on 2010-07-24
wvdial.gnome-ppp,pppconfig etc are for dialup.it wont work for DSL

---

