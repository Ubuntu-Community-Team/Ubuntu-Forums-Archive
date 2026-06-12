---
title: "HOWTO: disabling IPV6 support on your ubuntu linux and firefox internet browser"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by piju on 2008-02-12
tips for disabling ipv6 support on your ubuntu and firefox

first,

edit your /etc/modprobe.d/aliases using ur favourite text editor such as vim,nano or gedit

add this

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

and comment out this

#alias net-pf-10 ipv6

save quit,

open your firefox internet browser,

type about:config on the address bar

find ipv6

then disable ipv6 support, just twice click on it.

done.

p/s: dont forget to install fasterfox an addon for firefox

---

