---
title: "Connection freeze"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by Rhawi Dantas on 2005-05-03
I've just installed my Ubuntu 5.04 and configurated with pppoeconf as the howto in ubuntu site said...

Everything went normally and I add some repositories to it but then it starts to freeze the connection

Example: Using GAIM and downloading stuff and then I cant see web pages anymore just use GAIM... other time I was apt-getting java machine and suddenly i was unable to navigate anymore...

What should I do ?

I have an ADSL connection with a 3COM home connect modem...

---

### Post by Rhawi Dantas on 2005-05-03
I already fixed my problem

But for anyone that want to know I solved just editid

/etc/ppp/dsl-providers

uncomment the mtu line and set to 1412

preview from my file

```

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
mtu 1412
usepeerdns
plugin rp-pppoe.so eth0

```

---

