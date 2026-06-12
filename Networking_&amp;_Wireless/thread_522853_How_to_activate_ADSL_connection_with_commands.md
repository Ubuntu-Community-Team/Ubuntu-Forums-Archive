---
title: "How to activate ADSL connection with commands?"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by chunchengch on 2007-08-11
Sometimes, I forgot to turn on the ADSL modem or to plug the cable before I booted my laptop, and of course there would be no internet connection, at this moment, I turned on he ADSL modem or plugged the cable, the connection was still off, the only way for me was to reboot the laptop.

Few days ago, someone advised me to type following command to activate the ADSL connection, today, I got a chance to try it, while it did not work, should anyone tell me the proper commands? thanks a lot!

[COLOR="Red"]$ sudo pon dsl-provider[/COLOR]

the error message is
"The file /etc/ppp/peers/dsl-provider does not exist. Please create it or use
a command line argument to use another file in the /etc/ppp/peers/ directory."

here is the content of directories /etc/ppp and /etc/ppp/peers for reference.
@paul:/etc/ppp$ ls
chap-secrets ip-up ipv6-down.d options pppoe_on_boot
ip-down ip-up.d ipv6-up pap-secrets resolv
ip-down.d ipv6-down ipv6-up.d peers

@paul:/etc/ppp/peers$ ls
provider wvdial wvdial-pipe

---

### Post by linuxwizard on 2007-08-11
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

