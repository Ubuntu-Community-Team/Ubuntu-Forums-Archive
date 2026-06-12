---
title: "ipv6/networking issues"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by AndyRic on 2006-11-04
Hello all :) 

I am having Networking / ipv6 issues with my new ubuntu 6.10 installation and am at a bit of a loss.

First nothing would could connect to the outside world but disabling ipv6 in firefox with about:config allowed it to work and work well.

Unfortunately nothing else can get out!!

I have disabled ipv6 for the whole computer by editing /etc/modprobe.d/aliases with the addition of the following three lines and commenting the original :

[COLOR="Red"]alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off
#alias net-pf-10 ipv6 --> this was the original line
[/COLOR]
I have also created  a bad_list file in /etc/modprobe.d with the line

 [COLOR="Red"]alias net-pf-10 off[/COLOR]

in it to ensure that ipv6 is dead.

To confirm I have typed in :

[COLOR="Red"]ip a | grep inet6[/COLOR]

and the output is empty so ipv6 is disabled.

I have rebooted several times.

Still nothing but firefox (which runs beautifully) can connect to the internet.

I am behind a D-Link DSL-502T router.  Xandros and Windows work fine. 
Any suggestions?

---

### Post by el_ave on 2006-11-04
Hello,
Almost the exact same problem, minor differences are:
1. in /etc/modpobe.d/aliases I just changed one line from ```
alias net-pf-10 ipv6
``` to ```
alias net-pf-10 off
``` and it was sufficient to disable ipv6, at least ```
ip a | grep inet6
``` output was empty.
2. I did not create a bad_list file, but I added ```
blacklist ipv6
``` at the end of /etc/modprobe.d/blacklist (as far as I noticed this didn't change anything
3. I'm behind Dlink DSL-G604T

Hope someone can help!

---

### Post by el_ave on 2006-11-04
Some other (not Firefox) programs managed to connect to Internet:
[LIST=1]
[*]Gaim - icq did connect after several errors but msn doesn't connect
[*]Dictionary application is working
[*]Once apt-get update did succeed
[/LIST]

P.S. I haven't changed anything in my settings

---

### Post by el_ave on 2006-11-04
New strange thing I'm observing is that I can't install software using Applications -> Add/Remove... because it has problem connecting to servers but apt-get works fine :/

---

