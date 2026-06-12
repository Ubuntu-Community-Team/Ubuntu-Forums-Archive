---
title: "Ethernet with certificate"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by pittuzzo on 2008-10-07
I can't find a solution for my problem.

I live in a student's residence and we have an ethernet connection that uses a certificate.

There are instructions for windows, but not for linux system!

I can show you the configuration guide for window:
[http://www.asi.polimi.it/rete/navigazione/istruzioni/Configuration%20Guide%20Wired%20Windows%20XP%20ENG.doc](http://www.asi.polimi.it/rete/navigazione/istruzioni/Configuration%20Guide%20Wired%20Windows%20XP%20ENG.doc)

Can you help me to install this connection in Xubuntu?
waiting for answer....

Patrizio

---

### Post by willca on 2008-10-08
Have you tried to get your cert?

You can do this via firefox and it will do the import and all that stuff according to this doc (the part of certificate installation).

You will need to install wpa supplicant for this to work.

sudo apt-get install wpasupplicant

Edit /etc/network/interfaces

auto eth0
iface eth0 inet dhcp
wpa-driver wired
wpa-eap PEAP
wpa-key-mgmt IEEE8021X
wpa-identity your_identity
wpa-password your_password
wpa-ca-cert /etc/cert/ca.pem
wpa-phase1 peaplabel=1
wpa-phase2 auth=MSCHAPV2
wpa-priority 10

The file /etc/cert/ca.pem is the one you download on page one.
Just do the rest of the proxy stuff in your firefox.

Try it out and post the error message if ever.

---

