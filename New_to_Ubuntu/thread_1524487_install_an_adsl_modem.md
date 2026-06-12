---
title: "install an adsl modem"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by speedygarth on 2010-07-05
hi all i`m trying to share an internet connection using my linux server 9.04 installation and i`m using a ZISA modem which i bought recently, i`m still new to linux so the help will be appreciatted.

---

### Post by jpl888 on 2010-07-05
This is as simple or as complicated as you want it to be.

The simplest setup is this:-

Setup the DSL modem to connect to your provider.

Plug an ethernet cable from your Ubuntu machine in to the modem.

Unless you want a more complicated setup there should be nothing Ubuntu specific to doing this, so I would suggest looking at the modem's manual for information on how to set it up.

---

### Post by egalvan on 2010-07-05
> **speedygarth said:**
>  i`m trying to **share an internet connection**
 using my linux server 9.04 installation

Kinda vague there... exaclty what do you mean by ``share``?

Do you have more than one physical computer?

If so, are they now on a network?

How many network connections does your ZISA midem have?
being ad adsl type, it should have at minimum one connection for the dsl line (phone type) probably labeled INTERNET or WAN
 and one network connection for a computer, probably labeled NETWORK  or LAN 

more questions pop to mind, but they are dependant on your answers.

---

### Post by speedygarth on 2010-07-09
thanks for the replies guys, the modem actually has one ethernet connection and another usb connection which is currently plugged to a windows machine.
what i would like to achieve is to have the ubuntu server being the proxy server on my network so that the other macghine on the lan will get internet service from the linux server so that i can monitor the internet usage and finish up setting up the mail service as well.
i hope i have clarified or simplified my question.

thanks in advance.

---

### Post by jpl888 on 2010-07-09
Ok I have a lot of experience with this kind of setup since it is what I use for all my customers.

There are 2 ways of doing this with the type of modem you have, you can either:-

1. Connect the modem via the USB cable, use the RNDIS driver in the kernel and pppoe client on the Ubuntu machine.

2. Put an extra ethernet card in the Ubuntu machine and connect to the modem by that, again using the pppoe client in Ubuntu.

In both setups you may need to enable bridged mode on the modem YMMV RTFM.

In terms of the proxy setup I will tell you what I do; I have HAVP in transparent mode scanning all incoming traffic for viruses and OpenDNS (a bit of an Oxymoron if you ask me) providing content filtering. With the transparent setup you need firewall rules.

So once you've made a choice about which way you'd like it post back here asking for details and do it step by step.

---

### Post by speedygarth on 2010-07-12
thanks a lot, its all making sense now, anyway i plugged in an SMC network card and it was picked up during the bootup.

the problem now is i need to change the IP address of the new network card, as i only see the IP settings of the old card which comes up as Eth0 on IFconfig.
i think i need help with the pppoe client in Ubuntu setup.
and i also need help with configuring  bridged mode on the modem YMMV RTFM.

---

### Post by jpl888 on 2010-07-12
Change the IP address of eth1 in "/etc/network/interfaces" by copying the existing eth0 section and changing accordingly.

See below an example "/etc/ppp/peers/provider" and "/etc/ppp/chap-secrets" and change accordingly (hint nas0 would become eth1 if that is the ethernet interface you are connecting to the modem through):-

```
noipdefault
defaultroute
user 'vodafone@vodafone.ie'
noauth
updetach
#usepeerdns
plugin rp-pppoe.so
nas0

persist
maxfail 0
holdoff 10
lcp-max-configure 99
lcp-restart 30
lcp-echo-failure 1
lcp-echo-interval 30

### You may need to uncomment these
### options to connect with some ISP's.
### They disable compression.

noaccomp
nobsdcomp
nodeflate
nopcomp
noccp
novj

### If the firmware loads and pppd won't
### connect uncomment this option to make
### pppd be more verbose in the system log

debug

### For more details (and more options)
### Read man pppd

```      

```
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
vodafone@vodafone.ie    *       broadband

```

If you can't download the manual to find out out how to configure the modem in bridged (rfc 1483) mode perhaps you shouldn't be attempting this setup?

---

