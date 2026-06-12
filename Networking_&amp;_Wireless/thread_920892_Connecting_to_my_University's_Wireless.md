---
title: "Connecting to my University's Wireless"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by NickEvans on 2008-09-15
Hey,

My university uses WPA2 Enterprise authentication, and I can not connect under Ubuntu.

[Here]("http://www.ccs.uottawa.ca/connect/wireless/config-wpa-xp.html") are the instructions to configure wireless under XP. I'm new to WPA and to Linux wireless in general, so I would be grateful if someone could help me out. I would prefer if the solution could involve the nm-applet, because I still use it for connecting inside my residence.

---

### Post by satish_vell on 2008-09-15
Try [wicd]("http://wicd.sourceforge.net/")

And set it up using:
[http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=178](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=178)

You can use wicd at your home too.
Note: Wicd will uninstall NetworkManager(nm-applet)

---

### Post by Whiffle on 2008-09-15
I can do everything on that list with nm-applet up to the part about certificates.  nm-applet appears to not have a field for the PEAP authentication servers.  Unless someone knows more about that, I think your only option may be WICD.  You'll probably have to make a custom configuation file for WICD, but I bet its possible to make it work.

---

### Post by treymul on 2008-09-19
I am interested in this to.  I have been unable to connect to my universitys wireless.  I have tried xsupplicant and wpasupplicant without any luck.  Here are some of the errors:

TLS: Certificate verification failed, error 20 (unable to get local issuer certificate) depth 0 for '/C=US/ST=state/L=city/O=University
System/OU=Information Resources/CN=8021x.edu'
SSL: (where=0x4008 ret=0x230)
SSL: SSL3 alert: write (local SSL3 detected an error):fatal:unknown CA
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read server certificate B
OpenSSL: tls_connection_handshake - SSL_connect error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
SSL: 7 bytes pending from ssl_out
SSL: Failed - tls_out available to report error
SSL: 7 bytes left to be sent out (of total 7 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: heldWhile --> 0
RX EAPOL from mac address
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Failure
EAP: EAP entering state FAILURE
CTRL-EVENT-EAP-FAILURE EAP authentication failed

---

