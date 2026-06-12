---
title: "Problems with EAP-TTLS/MSCHAPV2"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Apo2k4 on 2008-03-04
Hi,
I'm trying to get my notebook to connect to my school's WLAN which is set up to use EAP-TTLS with MSCHAPV2.
Under Windows it's configured properly, so I know that it has to work somehow...

My wpa_supplicant.conf is this:

ctrl_interface=/var/run/wpa_supplicant
update_config=1

network={
        ssid="..."
        proto=RSN
#       key_mgmt=WPA-EAP
        key_mgmt=IEEE8021X
        pairwise=CCMP
        eap=TTLS
        identity="..."
        #anonymous_identity="anonymous@..."
        password="foobar"
        ca_cert="/etc/wpacacert.pem"
        phase2="auth=MSCHAPV2"
        id_str=".."
}

and /etc/network/interfaces:

allow-hotplug eth1
iface eth1 inet manual
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant.conf
iface ... inet dhcp

This is my WLAN card:
14:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

Some excerpts from the output of wpasupplicant -d

0: 00:90:4c:91:00:01 ssid='...' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:90:4c:91:00:01 ssid='...' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:90:4c:91:00:01 ssid='...'
Trying to associate with 00:90:4c:91:00:01 (SSID='...' freq=2462 MHz)
...
(It should have WPA, right? >_>)
...
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=2 method=21 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1003) - Flags 0x80
SSL: TLS Message Length: 993
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server hello A
TLS: Certificate verification failed, error 18 (self signed certificate) depth 0 for '/C=DE/ST=.../L=Bayreuth/O=.../OU=Organizational Unit Name (eg, section)/CN=.../emailAddress=root@...'
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
RX EAPOL from 00:90:4c:91:00:01
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Failure
EAP: EAP entering state FAILURE
CTRL-EVENT-EAP-FAILURE EAP authentication failed



At the same time, the radiusd reports
Tue Mar  4 16:05:45 2008 : Auth: Login incorrect: [Apo@.../<no User-Password attribute>] (from client ... port 4 cli 0013ce9aa739)

My password's obviously set, so what is wrong with it? Does wpasupplicant not send it? I really have no idea anymore :/

---

