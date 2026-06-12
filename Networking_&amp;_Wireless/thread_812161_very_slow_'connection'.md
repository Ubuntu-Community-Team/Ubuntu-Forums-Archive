---
title: "very slow 'connection'"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by xigen on 2008-05-29
In trying to get an avaya IP phone to work correctly our router (linksys wrtgl54) and modem got tweeked/unplugged (a lot).

my mac - works fine
my pc - works fine

my ubuntu 64/hardy box -- has a very slow network connection.

I have tried to re-boot (no luck)
reset the network connection: sudo ifdown eth0, sudo ifup eth0

...and no luck...

What process would you suggest I follow to get my network connection back?

-- yes, the ethernet cable is good and plugged in
-- router = OK, Modem =OK
-- ping [www.yahoo.com](www.yahoo.com) shows extremely slow response times. 

All the best... and thanks in advance.

---

### Post by alienexplorers on 2008-06-03
Have you tried to disable ipv6:
> # network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
#alias net-pf-10 ipv6 <---- Comment out this line
alias net-pf-11 rose
alias net-pf-12 decnet


---

### Post by garthqihe1 on 2011-01-13
> **xigen said:**
> In trying to get an avaya IP phone to work correctly our router (linksys wrtgl54) and modem got tweeked/unplugged (a lot).my mac - works finemy pc - works finemy ubuntu 64/hardy box -- has a very slow network connection.I have tried to re-boot (no luck)reset the network connection: sudo [[COLOR=#000000]ifdown[/COLOR]](http://www.sharit.biz/vi/sexuality/wife-cheated-has-your-wife-cheated-on-you.html) eth0, sudo ifup eth0...and no luck...What process would you suggest I follow to get my network connection back?-- yes, the ethernet cable is good and plugged in-- router=OK, Modem =OK-- ping [www.yahoo.com](http://www.yahoo.com) shows extremely slow response times. All the best... and thanks in advance.Now I understand more about it, Many thanks to your description!

---

