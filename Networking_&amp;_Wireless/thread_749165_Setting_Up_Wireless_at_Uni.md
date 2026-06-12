---
title: "Setting Up Wireless at Uni"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by ThinkDave on 2008-04-08
Ok so my wireless works fine on my WAP secured home network but im trying to set it up at the university this is the specs the uni needs for Windows XP.

SSID: ACHERNAR-BG

WAP
TKIP
PEAP
MSCHAPV2

Your uni userid and pass

and two thwate server certificates
Thwate Server CA
and
Thwate Premium Server CA

I've played around with the settings in ubuntu but cant seem to get it to work also is there anyway to add the two server certs cause at the moment i can only see how to use one. 
This is Wollongong Uni in Aus if anyone else has connected your help would be greatly appreciated.

---

### Post by kevdog on 2008-04-08
Take a look at this page and can you tell me which example closely resembles your network requirements?
[http://linux.die.net/man/5/wpa_supplicant.conf](http://linux.die.net/man/5/wpa_supplicant.conf)

---

### Post by ThinkDave on 2008-04-08
None of them The one with all examples is the closest. I listed all of what i needed in the first post.
I've been using network manager to connect but would it be possible to use wpa_supplicant.conf to set up two networks ie my home and my uni network?

Edit: on second look probably the first example with the two wireless networks but the settings for the Enterprise WAP are a bit off.

---

### Post by kevdog on 2008-04-08
Yes, its possible to put more than one network in the conf file, just put another network block.  The last example probably shouldn't be used since it contains everything.  You probably want to trim down the last example to meet your needs.  I'm surprised you university doesn't provide you an example or instructions on how to configure the conf file.  Most do -- if you talk to the correct person.  Each network is configured slightly differently, and without knowing an exact specification, we could try for hours, and miss a connection because we forgot one line.

---

### Post by ThinkDave on 2008-04-08
Uni doesn't support linux. Most of ITS staff know little about computers let alone linux and the people who would know are to busy to help. How do i activate this conf file as ive been using the GUI all this time im not sure of the conf file set up (that pages does help though thankyou)

---

### Post by kevdog on 2008-04-08
Take a look at this thread on how to manually connect, and then you are going to have to construct your wpa_supplicant.conf file somehow based on the previous link and the instructions on the page.  Kind of flying without a pilot at this stage.  

What exactly do you have?

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by ThinkDave on 2008-04-08
Do i have?
Got a Compaq laptop with a dlink 802.11b/g card that supports WAP.
Running Gutsy at least until the 24th.
An wireless is working got it connected to my home WAP connection at the moment so no problems there.
I just got some new CA certs from aptitude so maybe that was my problem ill try out the new certs tmrw and if that doesn't help ill go the conf file route.
Kinda hard to troubleshoot as im not at uni and can't test it.

---

### Post by kevdog on 2008-04-08
Was talking more about the ca certs and other things like possibly a username or password from the university.


Best to checkback when you can actually troubleshoot at the univerisity.  Good luck.

---

### Post by ThinkDave on 2008-04-09
Ok so im at uni now.
my driver is rt61pci i assume thats the wtext driver in wpa_supplicant.
I need to set up a wpa_supplicant.conf file
I need to log into a WPA network
with TKIP PEAP and MSCHAPV2

I need to have CA certs for
Thwate Premium Server CA
Thwate Server CA

I have the cert files i just need help making the conf file.

This is what i have so far

> ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

# home network;
network={
    ssid="RDSNetwork"
    scan_ssid=0
    key_mgmt=WPA-PSK
    psk="homepass"
}
#
# Uni network;
network={
    ssid="ACHERNAR-BG"
    scan_ssid=0
    key_mgmt=WPA-EAP
    pairwise=TKIP
    group=TKIP
    eap=PEAP
    identity=""
    password=""
    ca_cert="/usr/share/ca-certificates/mozilla/Thwate_Premium_Server_CA.crt"
    ca_cert2="/usr/share/ca-certificates/mozilla/Thwate_Server_CA.crt"
    phase1="peaplabel=0"
    phase2="auth=MSCHAPV2"
}


---

### Post by kevdog on 2008-04-09
Totally guessing but here  are some examples that I found:

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1
network={

    ssid="ZOR"
    key_mgmt=WPA-EAP
#    proto=RSN
#  pairwise=CCMP TKIP
#    group=CCMP TKIP
#    auth_alg=OPEN
   eap=PEAP
    identity="wireless"
    password="password"
    ca_cert="/etc/certs/cacert.pem"
#    phase1="peacap_outer_success=0"
#    phase1="peapver=1"
   phase1="peaplabel=1"
    phase2="auth=MSCHAPV2"
    priority=10
}  

Another example:

# IEEE 802.1X/EAPOL version
eapol_version=1

# AP scanning/selection
ap_scan=1

# EAP fast re-authentication
fast_reauth=0

#EAP-PEAP/MSCHAPv2 configuration for RADIUS servers that use the new peaplabel
#(e.g., Radiator)
network={
    ssid="UA_WPA"
    scan_ssid=1
    key_mgmt=WPA-EAP
    eap=PEAP
    pairwise=TKIP
    identity="<user>"
    password="<pass>"
    #ca_cert="/etc/cert/ca.pem"
    phase1="peaplabel=1"
    phase2="auth=MSCHAPV2"
    priority=7
    ap_scan=2
}

Or these:
        ctrl_interface=/var/run/wpa_supplicant
        ctrl_interface_group=root
        network={
              ssid="eduroam"
              scan_ssid=1
              key_mgmt=WPA-EAP
              eap=TTLS
              anonymous_identity="anonymous@uninett.no"
              ca_cert="/path/to/certificate/uninett-ca.crt"
              identity="brukernavn;
              password="password"
              phase1="peaplabel=0"
              phase2="auth=MSCHAPV2"
        }

Another configuration, almost identical to the above, only using PEAP:

        ctrl_interface=/var/run/wpa_supplicant
        ctrl_interface_group=localadm
        network={
              ssid="eduroam"
              key_mgmt=WPA-EAP
              eap=PEAP
              anonymous_identity="anonymous@uninett.no"
              ca_cert="/path/to/certificate/uninett-ca.crt"
              identity="brukernavn;
              password="password"
              phase2="auth=MSCHAPV2"
        }

Third alternative configuration that uses client certificate and EAP-TLS, and also certificate path to known CAs /etc/wpa_supplicant/certs instead of just one CA:

        ctrl_interface=/var/run/wpa_supplicant
        ctrl_interface_group=wheel
        network={
                ssid="eduroam"
                scan_ssid=0
                key_mgmt=WPA-EAP
                eap=TLS
                ca_path="/etc/wpa_supplicant/certs"
                client_cert="/path/to/client-crt.pem"
                private_key="/path/to/client-key.pem"
                identity="brukernavn@uninett.no"
        }


Again I dont know a lot about your setup or what is required.  It kind of a guessing game for me at this time.

---

### Post by ThinkDave on 2008-04-09
I said what it needed in the first post.
But im starting to think its a problem with the rt61pci drivers.
Its strange though WPA-PSK works fine.

---

### Post by kevdog on 2008-04-09
Are you using gutsy or another version?  That rt61pci driver is a pain in the butt.  Ive found the serial monkey rt61 driver better for gutsy and below.  In Hardy the rt2x00 driver replaces all the individual ra drivers.  Ive seen some report success, however since Hardy is in beta, the reports are sparse since the user base is small.

Any reason you are guessing its a rt61 driver problem?

---

### Post by ThinkDave on 2008-04-13
Because ive found a bunch of others here at uni who are connecting straight away with ubuntu using the gui. I also searched around and found a lot of problems with the rt61pci drivers. Maybe ill just wait for April 24th and try again with hardy.

Edit: Yeah i am using gutsy.

---

### Post by ThinkDave on 2008-05-07
Hardy solved the problem so i guess it was a problem with the drivers which have obviously been updated in hardy.

---

### Post by kevdog on 2008-05-07
Thanks for the update.  Could you mark the thread solved?

---

### Post by lexxonnet on 2008-05-07
Interestingly enough, I'm in the same uni as ThinkDave, and so far, the wireless has been patchy. On my old laptop(with an ipw2200 card), it worked quite well indeed, but on the newer one(iwl4965), it needs a lot of effort to keep it up and running.

For starters, network-manager doesn't connect to the wireless at all. I use wpa_supplicant and here's my config file.
```

ctrl_interface=/var/run/wpa_supplicant ctrl_interface_group=0

eapol_version=2
ap_scan=1
fast_reauth=1

network={
        ssid="ACHERNAR-BG"
        key_mgmt=WPA-EAP
        proto=WPA
        eap=PEAP
        pairwise=TKIP
        group=TKIP
        identity="*****"
        password="********"
        ca_cert="/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
        phase1="peaplabel=0" include_tls_length=1"
        phase2="auth=MSCHAPV2"
        priority=1
        scan_ssid=1
}

```
All the access points in uni use a hidden ssid, and I think this causes some problems in itself. The only way I ever connect, is by initially setting the ap_scan mode to 2 first, and then running wpa_supplicant for a while. Then, kill it, set ap_scan to 1, and then connect, and it may or may not work.

The main issue seems to be that half the time, it authenticates, and the other half, it doesn't. I'm not sure what the issue is to be honest.

I also tried on a friend's laptop which has an atheros card. Network Manager seems to connect fine there, but it drops off after a while. Same with wpa_supplicant (after doing the ap_scan switching thing, doesn't work otherwise). With the atheros card however, it always authenticates fine, though it disconnects after 5-10 minutes.

Does anyone else have issues such as this? If so... any ideas?

---

### Post by kevdog on 2008-05-08
I wish I could help you with this one --- obviously something is afoul.  Not sure if its a driver issue, or a hidden essid issue -- annoying however.

---

### Post by lexxonnet on 2008-05-08
Hehe... it is indeed!

It could be a hidden essid issue. I should update my old laptop to hardy and see if it still works with ipw2200. There's apparently been a lot of changes in the wireless stack in the more recent kernels, so it might just be that messing around with it.

AFAIK, I've tried it on my iwl4965 and a random atheros card, and both of them have issues connecting to the uni wireless. Basically, the atheros connects but keeps dropping off, while the intel has issues to begin with. I might just post some relevant output from wpa_supplicant here in the hope that some kind passing soul will see it and chance upon a solution :)

---

### Post by lexxonnet on 2008-05-08
This is verbose output from wpa_supplicant when it doesn't authenticate with the server. 

```

State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0f:23:26:ef:60
No keys have been configured - skip key clearing
Associated with 00:0f:23:26:ef:60
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:0f:23:26:ef:60
RX EAPOL - hexdump(len=60): 01 00 00 38 01 01 00 38 01 00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52 4e 41 52 2d 42 47 2c 6e 61 73 
69 64 3d 42 33 35 53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69 64 3d 30
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=51):
     00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52   _networkid=ACHER
     4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35   NAR-BG,nasid=B35
     53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69   SAP1ag.net,porti
     64 3d 30                                          d=0
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 02 00 00 0a 02 01 00 0a 01 61 6d 33 39 34
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: startWhen --> 0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 1670 bytes of scan results (8 BSSes)
Scan results: 8
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:26:f5:20 ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch

```

As seen above, it never succeeds in authenticating with the EAP server. Now, here is a case when it does.

```

State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0d:bc:50:67:4c
No keys have been configured - skip key clearing
Associated with 00:0d:bc:50:67:4c
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=60): 01 00 00 38 01 01 00 38 01 00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52 4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 36 37 41 50 31 37 61 67 2e 6e 65 74 2c 70 6f 72 74 69 64 3d 30
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=51):
     00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52   _networkid=ACHER
     4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 36 37   NAR-BG,nasid=B67
     41 50 31 37 61 67 2e 6e 65 74 2c 70 6f 72 74 69   AP17ag.net,porti
     64 3d 30                                          d=0
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 02 00 00 0a 02 01 00 0a 01 61 6d 33 39 34
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=46): 01 00 00 15 01 29 00 15 11 01 00 08 80 26 bb c5 68 21 ff a2 61 6d 33 39 34 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=41 method=17 vendor=0 vendorMethod=0
EAP: EAP entering state GET_METHOD
EAP: configuration does not allow: vendor 0 method 17
EAP: vendor 0 method 17 not allowed
EAP: Building EAP-Nak (requested type 17 vendor=0 method=0 not allowed)
EAP: allowed methods - hexdump(len=1): 19
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=10): 02 00 00 06 02 29 00 06 03 19
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=46): 01 00 00 06 01 2a 00 06 19 21 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=42 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state GET_METHOD
EAP: Initialize selected EAP method: vendor 0 method 25 (PEAP)
EAP-PEAP: Phase2 EAP types - hexdump(len=8): 00 00 00 00 1a 00 00 00
TLS: Trusted root certificate(s) loaded
TLS: Include TLS Message Length in unfragmented packets
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
EAP: EAP entering state METHOD
SSL: Received packet(len=6) - Flags 0x21
EAP-PEAP: Start (server ver=1, own ver=1)
EAP-PEAP: Using PEAP version 1
SSL: (where=0x10 ret=0x1)
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:before/connect initialization
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client hello A
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read server hello A
SSL: SSL_connect - want more data
SSL: 87 bytes pending from ssl_out
SSL: 87 bytes left to be sent out (of total 87 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=101): 02 00 00 61 02 2a 00 61 19 81 00 00 00 57 16 03 01 00 52 01 00 00 4e 03 01 48 02 cd 6a 61 bc 6b 83 c3 f1 3c ca f2 d8 1d be e2 ad 80 18 5f 94 19 ed a4 fa 54 56 11 96 70 c1 00 00 26 00 39 00 38 00 35 00 16 00 13 00 0a 00 33 00 32 00 2f 00 05 00 04 00 15 00 12 00 09 00 14 00 11 00 08 00 06 00 03 02 01 00
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=1016): 01 00 03 f4 01 2b 03 f4 19 c1 00 00 07 bf 16 03 01 00 4a 02 00 00 46 03 01 48 02 cd 63 cb 66 2d 56 61 56 0b 64 04 a4 8c 80 6c 09 5d 72 e4 50 09 1e 29 3d 4d a0 bf d8 95 20 20 44 4f ad 0d 77 e0 35 df 16 d1 59 3d 73 d6 cb d6 97 58 a6 5e 74 3f 0a b4 d2 61 3d e3 69 15 4e 5a 00 35 00 16 03 01 07 62 0b 00 07 5e 00 07 5b 00 04 2a 30 82 04 26 30 82 03 8f a0 03 02 01 02 02 10 76 b4 32 52 e2 93 bb 5b 94 6e 11 11 63 16 9f b2 30 0d 06 09 2a 86 48 86 f7 0d 01 01 05 05 00 30 81 ce 31 0b 30 09 06 03 55 04 06 13 02 5a 41 31 15 30 13 06 03 55 04 08 13 0c 57 65 73 74 65 72 6e 20 43 61 70 65 31 12 30 10 06 03 55 04 07 13 09 43 61 70 65 20 54 6f 77 6e 31 1d 30 1b 06 03 55 04 0a 13 14 54 68 61 77 74 65 20 43 6f 6e 73 75 6c 74 69 6e 67 20 63 63 31 28 30 26 06 03 55 04 0b 13 1f 43 65 72 74 69 66 69 63 61 74 69 6f 6e 20 53 65 72 76 69 63 65 73 20 44 69 76 69 73 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 54 68 61 77 74 65 20 50 72 65 6d 69 75 6d 20 53 65 72 76 65 72 20 43 41 31 28 30 26 06 09 2a 86 48 86 f7 0d 01 09 01 16 19 70 72 65 6d 69 75 6d 2d 73 65 72 76 65 72 40 74 68 61 77 74 65 2e 63 6f 6d 30 1e 17 0d 30 37 31 31 30 36 32 33 32 36 32 36 5a 17 0d 30 38 31 31 30 35 32 33 32 36 32 36 5a 30 81 a6 31 0b 30 09 06 03 55 04 06 13 02 41 55 31 18 30 16 06 03 55 04 08 13 0f 4e 65 77 20 53 6f 75 74 68 20 57 61 6c 65 73 31 13 30 11 06 03 55 04 07 13 0a 57 6f 6c 6c 6f 6e 67 6f 6e 67 31 21 30 1f 06 03 55 04 0a 13 18 55 6e 69 76 65 72 73 69 74 79 20 6f 66 20 57 6f 6c 6c 6f 6e 67 6f 6e 67 31 28 30 26 06 03 55 04 0b 13 1f 49 6e 66 6f 72 6d 61 74 69 6f 6e 20 54 65 63 68 6e 6f 6c 6f 67 79 20 53 65 72 76 69 63 65 73 31 1b 30 19 06 03 55 04 03 13 12 63 73 65 63 2e 61 64 2e 75 6f 77 2e 65 64 75 2e 61 75 30 82 01 22 30 0d 06 09 2a 86 48 86 f7 0d 01 01 01 05 00 03 82 01 0f 00 30 82 01 0a 02 82 01 01 00 ac e6 d8 e2 c5 db 3b 6e 44 3a 79 1f 01 da eb b5 98 14 f3 cc 2d 3f 5a 78 c2 42 cb 0b 62 35 d1 34 d4 be 4f da 77 d7 d8 a0 67 87 78 09 b1 1c 64 fc 7c 9e 1c b7 fd 45 1f 89 7a 41 3d d8 0b 41 4c 4d d0 82 e1 0b 70 c1 94 5f ae 58 77 46 b2 00 6e d3 1a 3b c5 c5 11 e0 a1 29 a7 57 92 ee c1 c6 ed b6 9a ab 3a bd 72 59 ba 26 79 93 2a 14 e2 87 d2 63 d2 9a 83 17 b7 04 66 54 5c f2 66 35 3d 45 47 38 9f 3a 06 77 6f 34 db 49 06 cd 54 3f 6f 83 2e a3 63 67 29 b5 80 46 db d5 6d bb 7b 55 63 95 da ca 34 db 64 a3 54 99 38 b7 b9 3a d3 5e bb 50 d7 75 97 d5 57 52 4a 3e 69 3c 7d c6 83 37 30 95 5c d8 db 65 76 0c ee af dc 4f 3f e2 82 05 e0 b8 20 f2 d7 10 e0 d9 e3 b0 92 b6 af c1 77 cd 62 87 d2 f6 88 dc 73 61 34 70 fa 00 80 38 a1 07 01 6f 02 a9 dd c1 cf 04 2a 8a b2 25 cf 80 21 27 ba 3b a9 c3 02 03 01 00 01 a3 81 a6 30 81 a3 30 1d 06 03 55 1d 25 04 16 30 14 06 08 2b 06 01 05 05 07 03 01 06 08 2b 06 01 05 05 07 03 02 30 40 06 03 55 1d 1f 04 39 30 37 30 35 a0 33 a0 31 86 2f 68 74 74 70 3a 2f 2f 63 72 6c 2e 74 68 61 77 74 65 2e 63 6f 6d 2f 54 68 61 77 74 65 50 72 65 6d 69 75 6d 53 65 72 76 65 72 43 41 2e 63 72 6c 30 32 06 08 2b 06 01 05 05 07 01 01 04 26 30 24 30 22 06 08 2b 06 01 05 05 07 30 01 86 16 68 74 74 70 3a 2f 2f 6f 63 73 70 2e 74 68 61 77 74 65 2e 63 6f 6d 30 0c 06
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=43 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1012) - Flags 0xc1
SSL: TLS Message Length: 1983
SSL: Need 981 bytes more input data
SSL: Building ACK
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=10): 02 00 00 06 02 2b 00 06 19 01
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=991): 01 00 03 db 01 2c 03 db 19 01 03 55 1d 13 01 01 ff 04 02 30 00 30 0d 06 09 2a 86 48 86 f7 0d 01 01 05 05 00 03 81 81 00 92 09 00 ac a3 eb f5 f7 94 d6 cd 24 dc 8a bc eb 04 44 64 6e 1b a9 1d 8b 12 5d c4 98 7c b6 b7 5e 1e a5 5d da b1 85 56 44 c2 bb 53 4f bd f5 2d a1 5d a0 31 13 5b c7 33 43 00 f2 7c 36 fb 0e 62 c5 14 94 ed 2b d2 9a 1c 90 e8 cf a9 e7 06 4b 97 9e 0b 16 84 a5 cd d4 e9 21 fd 68 5a 7b d7 8a 42 c4 db 9c a9 1b 15 ac 56 f8 20 48 c1 a0 22 b4 69 9c 62 b1 53 94 df 9c 18 ba b4 51 c4 a7 53 99 e2 41 00 03 2b 30 82 03 27 30 82 02 90 a0 03 02 01 02 02 01 01 30 0d 06 09 2a 86 48 86 f7 0d 01 01 04 05 00 30 81 ce 31 0b 30 09 06 03 55 04 06 13 02 5a 41 31 15 30 13 06 03 55 04 08 13 0c 57 65 73 74 65 72 6e 20 43 61 70 65 31 12 30 10 06 03 55 04 07 13 09 43 61 70 65 20 54 6f 77 6e 31 1d 30 1b 06 03 55 04 0a 13 14 54 68 61 77 74 65 20 43 6f 6e 73 75 6c 74 69 6e 67 20 63 63 31 28 30 26 06 03 55 04 0b 13 1f 43 65 72 74 69 66 69 63 61 74 69 6f 6e 20 53 65 72 76 69 63 65 73 20 44 69 76 69 73 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 54 68 61 77 74 65 20 50 72 65 6d 69 75 6d 20 53 65 72 76 65 72 20 43 41 31 28 30 26 06 09 2a 86 48 86 f7 0d 01 09 01 16 19 70 72 65 6d 69 75 6d 2d 73 65 72 76 65 72 40 74 68 61 77 74 65 2e 63 6f 6d 30 1e 17 0d 39 36 30 38 30 31 30 30 30 30 30 30 5a 17 0d 32 30 31 32 33 31 32 33 35 39 35 39 5a 30 81 ce 31 0b 30 09 06 03 55 04 06 13 02 5a 41 31 15 30 13 06 03 55 04 08 13 0c 57 65 73 74 65 72 6e 20 43 61 70 65 31 12 30 10 06 03 55 04 07 13 09 43 61 70 65 20 54 6f 77 6e 31 1d 30 1b 06 03 55 04 0a 13 14 54 68 61 77 74 65 20 43 6f 6e 73 75 6c 74 69 6e 67 20 63 63 31 28 30 26 06 03 55 04 0b 13 1f 43 65 72 74 69 66 69 63 61 74 69 6f 6e 20 53 65 72 76 69 63 65 73 20 44 69 76 69 73 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 54 68 61 77 74 65 20 50 72 65 6d 69 75 6d 20 53 65 72 76 65 72 20 43 41 31 28 30 26 06 09 2a 86 48 86 f7 0d 01 09 01 16 19 70 72 65 6d 69 75 6d 2d 73 65 72 76 65 72 40 74 68 61 77 74 65 2e 63 6f 6d 30 81 9f 30 0d 06 09 2a 86 48 86 f7 0d 01 01 01 05 00 03 81 8d 00 30 81 89 02 81 81 00 d2 36 36 6a 8b d7 c2 5b 9e da 81 41 62 8f 38 ee 49 04 55 d6 d0 ef 1c 1b 95 16 47 ef 18 48 35 3a 52 f4 2b 6a 06 8f 3b 2f ea 56 e3 af 86 8d 9e 17 f7 9e b4 65 75 02 4d ef cb 09 a2 21 51 d8 9b d0 67 d0 ba 0d 92 06 14 73 d4 93 cb 97 2a 00 9c 5c 4e 0c bc fa 15 52 fc f2 44 6e da 11 4a 6e 08 9f 2f 2d e3 f9 aa 3a 86 73 b6 46 53 58 c8 89 05 bd 83 11 b8 73 3f aa 07 8d f4 42 4d e7 40 9d 1c 37 02 03 01 00 01 a3 13 30 11 30 0f 06 03 55 1d 13 01 01 ff 04 05 30 03 01 01 ff 30 0d 06 09 2a 86 48 86 f7 0d 01 01 04 05 00 03 81 81 00 26 48 2c 16 c2 58 fa e8 16 74 0c aa aa 5f 54 3f f2 d7 c9 78 60 5e 5e 6e 37 63 22 77 36 7e b2 17 c4 34 b9 f5 08 85 fc c9 01 38 ff 4d be f2 16 42 43 e7 bb 5a 46 fb c1 c6 11 1f f1 4a b0 28 46 c9 c3 c4 42 7d bc fa ab 59 6e d5 b7 51 88 11 e3 a4 85 19 6b 82 4c a4 0c 12 ad e9 a4 ae 3f f1 c3 49 65 9a 8c c5 c8 3e 25 b7 94 99 bb 92 32 71 07 f0 86 5e ed 50 27 a6 0d a6 23 f9 bb cb a6 07 14 42 16 03 01 00 04 0e 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=44 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=987) - Flags 0x01
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server hello A
TLS: tls_verify_cb - preverify_ok=1 err=0 (ok) depth=1 buf='/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com'
TLS: tls_verify_cb - preverify_ok=1 err=0 (ok) depth=0 buf='/C=AU/ST=New South Wales/L=Wollongong/O=University of Wollongong/OU=Information Technology Services/CN=csec.ad.uow.edu.au'
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server certificate A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server done A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client key exchange A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write change cipher spec A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write finished A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 flush data
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read finished A
SSL: SSL_connect - want more data
SSL: 326 bytes pending from ssl_out
SSL: 326 bytes left to be sent out (of total 326 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=340): 02 00 01 50 02 2c 01 50 19 81 00 00 01 46 16 03 01 01 06 10 00 01 02 01 00 7e 14 e4 8d 52 d1 37 38 a2 83 09 26 01 f9 a4 a3 73 62 65 a3 15 b9 f6 f5 ae 60 8d ac 1e 55 3e a2 f8 ea 68 cb ab c5 9a 65 cb 15 18 8a cd 96 4a 1c 15 b2 12 86 c0 77 9d e2 51 06 1b b4 37 18 bc d1 f8 df d7 e8 67 e7 6c a0 f8 10 7a 3b d5 2a 04 51 b1 18 05 5b b8 63 fc bb 03 b9 88 6d a7 be ba 47 75 ff 86 4a 86 c6 78 59 b1 6a 7e f9 cc 9f 9f 05 2b ff b5 d0 12 f0 ad be de a2 dd 92 df 5c cc a0 8b 94 f1 2a 91 e2 51 98 b2 1c 09 9c 4e d9 e9 9e 4f ea 23 d6 41 50 1f 63 05 05 6a a3 66 f4 e2 01 a2 11 ba 60 8c b5 b1 ec 93 69 66 8a e7 38 41 bc 18 32 8d 6f 27 19 6d 42 f8 be 77 a4 f8 22 f4 63 cf 9f 41 a7 94 f4 24 3e 85 68 0d 28 b9 78 48 f9 ae 46 53 73 be 74 a4 32 59 09 57 2a d3 5f 9e 72 fc ea d6 6c f9 d8 7c bc 4e de c1 40 cf 17 f0 93 30 01 83 14 e4 03 c3 70 57 65 a8 a4 19 bc eb 1d 14 03 01 00 01 01 16 03 01 00 30 29 7c 6d 7c 4e 6d b6 67 6b 2e 2e ca b7 3e 76 06 0b 76 42 f5 38 3f ce 8e 1f 21 43 7c f7 59 c2 84 f5 36 58 12 59 9c 70 e5 9b c5 bb 2f 4a 65 8f 17
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=73): 01 00 00 45 01 2d 00 45 19 81 00 00 00 3b 14 03 01 00 01 01 16 03 01 00 30 6c f9 8c e5 db 79 58 6a 64 20 31 28 75 49 6f a2 e6 ab c1 b4 83 f4 3e d4 21 80 8b b7 86 99 ef 02 fc 4c 8f ec b0 f8 3d 9e a2 a0 a2 a1 8c da 9d c2
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=45 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=69) - Flags 0x81
SSL: TLS Message Length: 59
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read finished A
SSL: (where=0x20 ret=0x1)
SSL: (where=0x1002 ret=0x1)
SSL: 0 bytes pending from ssl_out
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
SSL: No data to be sent out
EAP-PEAP: TLS done, proceed to Phase 2
EAP-PEAP: using label 'client EAP encryption' in key derivation
EAP-PEAP: Derived key - hexdump(len=64): [REMOVED]
SSL: Building ACK
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=10): 02 00 00 06 02 2d 00 06 19 01
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=47): 01 00 00 2b 01 2e 00 2b 19 01 17 03 01 00 20 94 c6 7b f2 7a b0 f0 96 3e 24 89 74 32 07 c9 35 7e a2 41 bd 0f 5b a6 b8 83 d9 da a0 71 48 65 cf
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=46 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=43) - Flags 0x01
EAP-PEAP: received 37 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=5): 01 46 00 05 01
EAP-PEAP: received Phase 2: code=1 identifier=70 length=5
EAP-PEAP: Phase 2 Request: type=1
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=10): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 2e 00 50 19 01 17 03 01 00 20 c4 ee 8a ab 00 df 7b 90 48 93 ad 7b 32 cc 8e bb 6b d4 ed 6d e1 80 19 99 be a9 05 d8 cf 23 2b 96 17 03 01 00 20 7e f6 81 84 76 63 62 7d 67 03 aa eb 79 60 9a af d3 95 80 c3 c8 ae 2b a4 8b c4 b2 f6 da 45 7e 32
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=63): 01 00 00 3b 01 2f 00 3b 19 01 17 03 01 00 30 c1 b1 e7 75 3d fe 9f 47 51 63 0d bb 9f f6 75 2f 8d a5 43 6d e6 95 97 a6 cc 91 1e 79 0a 71 bb f7 5f 9d 3c 7d 2d d3 0d 64 57 3b 2d 15 00 08 45 4f
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=47 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=59) - Flags 0x01
EAP-PEAP: received 53 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=24): 01 47 00 18 06 45 6e 74 65 72 20 79 6f 75 72 20 70 61 73 73 77 6f 72 64
EAP-PEAP: received Phase 2: code=1 identifier=71 length=24
EAP-PEAP: Phase 2 Request: type=6
EAP-PEAP: Phase 2 Request: Nak type=6
EAP-PEAP: Allowed Phase2 EAP types - hexdump(len=8): 00 00 00 00 1a 00 00 00
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=6): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 2f 00 50 19 01 17 03 01 00 20 69 76 5e b0 d9 33 76 cc 14 f3 52 f3 a5 d3 3d 78 59 ff 81 e1 67 e7 7a ba 74 29 68 c7 87 1d 12 66 17 03 01 00 20 89 72 a9 c3 c3 74 4b 36 83 75 dd 52 16 c1 36 1e e7 24 1d 06 45 a7 d3 50 52 2a c8 d6 ff ea 2c d7
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=79): 01 00 00 4b 01 30 00 4b 19 01 17 03 01 00 40 34 90 ea 8d 57 c9 05 1b 58 97 4b bc 11 09 ae 26 45 26 a3 4d a1 1d 2b c7 5c a5 92 e4 7d 45 f4 22 13 c8 16 a3 91 b0 b9 64 11 8b d1 8f f1 73 82 12 c9 3e 25 fd 7c 2b 07 47 07 96 09 2d 79 56 32 a1
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=48 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=75) - Flags 0x01
EAP-PEAP: received 69 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=31): 01 48 00 1f 1a 01 48 00 1a 10 24 76 a9 73 86 fe b7 2f 82 c2 f4 63 1d d4 f2 b3 43 53 45 43 31
EAP-PEAP: received Phase 2: code=1 identifier=72 length=31
EAP-PEAP: Phase 2 Request: type=26
EAP-PEAP: Selected Phase 2 EAP vendor 0 method 26
EAP-MSCHAPV2: RX identifier 72 mschapv2_id 72
EAP-MSCHAPV2: Received challenge
EAP-MSCHAPV2: Authentication Servername - hexdump_ascii(len=5):
     43 53 45 43 31                                    CSEC1
EAP-MSCHAPV2: Generating Challenge Response
EAP-MSCHAPV2: auth_challenge - hexdump(len=16): 24 76 a9 73 86 fe b7 2f 82 c2 f4 63 1d d4 f2 b3
EAP-MSCHAPV2: peer_challenge - hexdump(len=16): c7 e5 d1 51 f7 f5 45 71 69 8d 03 2c 17 c7 65 5b
EAP-MSCHAPV2: username - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP-MSCHAPV2: password - hexdump_ascii(len=8): [REMOVED]
EAP-MSCHAPV2: response - hexdump(len=24): ff 3c 55 22 c4 21 9a 0e f5 3c 56 fb 34 1e a6 ec dc 42 33 8e 49 eb aa 7b
EAP-MSCHAPV2: TX identifier 72 mschapv2_id 72 (response)
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=64): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=148): 02 00 00 90 02 30 00 90 19 01 17 03 01 00 20 67 7a 07 d9 78 a1 ac 29 c1 0e 21 55 dd 9d ac 64 7a 01 f4 f9 3c e7 78 67 77 a6 99 f6 90 eb 02 b9 17 03 01 00 60 10 7c 7a 4b 21 ca 52 77 aa 11 4b fd a3 76 80 06 0c 6b f4 1e 80 86 d2 50 50 b3 e7 db e3 f6 44 ec bc db 9d 42 ac 8f c2 de b6 32 21 a7 92 30 5c 14 4f 82 52 c1 56 82 46 92 f7 7b 16 c3 51 36 c5 94 d8 3d 29 6f bf c9 95 65 88 86 8e 09 5a fb 1a ee 11 43 ed c2 b7 74 81 09 e2 b5 04 36 ad 4a f5 3b
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=95): 01 00 00 5b 01 31 00 5b 19 01 17 03 01 00 50 30 77 d1 9c cf 9d 95 77 0a 8c 95 6e ed 0b bd 93 99 51 ea 12 9c b8 2c 53 8f c6 f6 67 b7 48 91 6a e5 72 81 c3 de e7 eb 89 80 69 73 33 c3 48 bb ae 6f 3a 5e a1 c6 22 0c 87 5c 3b 5e 8f ae f3 63 8d 9b ee e0 88 ea 47 91 bf 10 f1 e4 2b be cf fa 25
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=49 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=91) - Flags 0x01
EAP-PEAP: received 85 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=51): 01 49 00 33 1a 03 48 00 2e 53 3d 43 45 44 45 35 30 38 37 32 46 44 44 43 42 45 37 41 38 35 36 38 42 31 32 31 42 33 39 33 45 46 39 45 43 38 46 36 32 35 37
EAP-PEAP: received Phase 2: code=1 identifier=73 length=51
EAP-PEAP: Phase 2 Request: type=26
EAP-MSCHAPV2: RX identifier 73 mschapv2_id 72
EAP-MSCHAPV2: Received success
EAP-MSCHAPV2: Success message - hexdump_ascii(len=0):
EAP-MSCHAPV2: Authentication succeeded
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=6): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 31 00 50 19 01 17 03 01 00 20 a1 8d 33 54 2c f8 5a 24 1d 0b fc 52 17 1a ad 3b 75 de 98 30 c0 cc 2c 25 6a bc 3b c6 2c 05 a1 45 17 03 01 00 20 c5 1f 55 8d 04 47 03 e4 16 7c e4 51 be 0f 8e ee c4 f0 1f 76 3f f9 e9 00 82 e1 88 c8 74 4b 42 9f
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=47): 01 00 00 2b 01 32 00 2b 19 01 17 03 01 00 20 ad da 4b 97 e3 4b 3b bf 09 76 1b 1e f4 ec 0a ed 58 50 97 e6 a8 df c6 a5 1f c7 47 4a 94 57 20 af
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=50 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=43) - Flags 0x01
EAP-PEAP: received 37 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=11): 01 4a 00 0b 21 80 03 00 02 00 01
EAP-PEAP: received Phase 2: code=1 identifier=74 length=11
EAP-PEAP: Phase 2 Request: type=33
EAP-TLV: Received TLVs - hexdump(len=6): 80 03 00 02 00 01
EAP-TLV: Result TLV - hexdump(len=2): 00 01
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=11): [REMOVED]
EAP: method process -> ignore=FALSE methodState=DONE decision=UNCOND_SUCC
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 32 00 50 19 01 17 03 01 00 20 ab db 2a 78 a6 05 ee 3c b2 6a 13 43 35 2a 23 05 2a b6 f6 90 20 5c 20 67 53 85 67 82 2b f1 da 8d 17 03 01 00 20 f2 c7 7e b2 a4 81 da 43 04 cc 55 45 77 de 72 e6 5e d4 b6 9f d8 09 26 12 b6 f4 d2 0b 40 81 77 f2
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=46): 01 00 00 04 03 32 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Success
EAP: EAP entering state SUCCESS
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_BE entering state IDLE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fe 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fe
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fe 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:0d:bc:50:67:4c (ver=1)
WPA: PMK from EAPOL state machines - hexdump(len=32): [REMOVED]
WPA: Renewed SNonce - hexdump(len=32): a8 6b 17 6b 89 5a a7 df 3a e3 9b aa 12 84 00 31 65 1a c0 cd b6 41 49 9c 83 f7 c1 47 a8 66 72 5d
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 02 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 a8 6b 17 6b 89 5a a7 df 3a e3 9b aa 12 84 00 31 65 1a c0 cd b6 41 49 9c 83 f7 c1 47 a8 66 72 5d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8c 3d 73 f8 08 7f 18 21 95 c2 e7 83 6c 82 e9 6e 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fe 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8f c5 00 9f 90 fe be 74 70 bd 04 65 8b ae 3f b1 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=26
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fe
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 8f c5 00 9f 90 fe be 74 70 bd 04 65 8b ae 3f b1
WPA: RX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fe 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8f c5 00 9f 90 fe be 74 70 bd 04 65 8b ae 3f b1 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:0d:bc:50:67:4c (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 02 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fa 21 89 da 28 0f a5 d2 93 83 45 20 13 f5 ff 26 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:0d:bc:50:67:4c
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 03 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fc 5c 50 3a cc e6 bb 0c ea af df a0 fd 50 fe ca 7e 12 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a4 b4 b3 59 4b 1c 29 66 e0 cd 54 fd 48 a2 e2 74 00 20 1b bb ab bd bc 3b 20 51 72 d3 e4 12 56 0c 22 4b 98 42 3b 18 7b c3 83 ed 8d 8e df 93 9d 6d ac 5a
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fc
  key_iv - hexdump(len=16): 5c 50 3a cc e6 bb 0c ea af df a0 fd 50 fe ca 7e
  key_rsc - hexdump(len=8): 12 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): a4 b4 b3 59 4b 1c 29 66 e0 cd 54 fd 48 a2 e2 74
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 03 85 45 b9 61 f0 ad 99 ee 4a be 41 1b 77 82 ba df 73 e9 ec f6 b9 36 9e 18 1a 2b 86 de a0 f8 27 fc 5c 50 3a cc e6 bb 0c ea af df a0 fd 50 fe ca 7e 12 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a4 b4 b3 59 4b 1c 29 66 e0 cd 54 fd 48 a2 e2 74 00 20 1b bb ab bd bc 3b 20 51 72 d3 e4 12 56 0c 22 4b 98 42 3b 18 7b c3 83 ed 8d 8e df 93 9d 6d ac 5a
WPA: RX message 1 of Group Key Handshake from 00:0d:bc:50:67:4c (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0).
WPA: RSC - hexdump(len=6): 12 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 02 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fd 40 47 f9 2e f2 2f 9b 2c 57 37 21 e4 ff bb 9c 00 00
WPA: Key negotiation completed with 00:0d:bc:50:67:4c [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
Removed BSSID 00:0d:bc:50:67:4c from blacklist
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:0d:bc:50:67:4c completed (auth) [id=0 id_str=]

```

Yup... its a lot longer, and it seems to first authenticate with eap, and then proceed to phase2 authentication(with mschapv2) and then do a 4 way group handshake or something of the sort. Basically, when this happens once in a while, I rejoice.

Then, sometimes, this happens
```

CTRL-EVENT-CONNECTED - Connection to 00:0d:bc:50:67:4c completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: SUPP_PAE entering state AUTHENTICATED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 2
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: startWhen --> 0
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 1399 bytes of scan results (7 BSSes)
Scan results: 7
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0d:28:af:0f:92 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0d:bc:50:67:4e ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:0d:bc:50:67:4e ssid='ACHERNAR-BG'
Try to find non-WPA AP
Trying to associate with 00:0d:bc:50:67:4e (SSID='ACHERNAR-BG' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_drop_unencrypted
State: COMPLETED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=19
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=149
WEXT: Custom wireless event:

```

Seems to disconnect soon after it authenticates. Weird thing is, when it authenticates, its great. I get an ip with dhclient and everything works smoothly for a while. Half the time, it stays authenticated, but the other half, it just kills itself.

---

### Post by kevdog on 2008-05-08
Might need to play around with some of the setting ins the wpa_supplicant.conf file.  Then again could be a driver issue.  I don't know.  This new hardy kernel is terrible in terms of wireless support -- it just flats out stinks.  I heard the new kernel (or newest vanilla kernel) is better, but that is just rumor.  A lot of the problems were solved.  I think Hardy's biggest failure is the kernel it is built upon.  Definitely no long term solution.

---

### Post by lexxonnet on 2008-05-08
> **kevdog said:**
> Might need to play around with some of the setting ins the wpa_supplicant.conf file.  Then again could be a driver issue.  I don't know.  This new hardy kernel is terrible in terms of wireless support -- it just flats out stinks.  I heard the new kernel (or newest vanilla kernel) is better, but that is just rumor.  A lot of the problems were solved.  I think Hardy's biggest failure is the kernel it is built upon.  Definitely no long term solution.

Yeah, I have a feeling its either a driver or a kernel issue. As I said, I'm probably going to hardify my old lappy over the weekend(its running gutsy at the moment), and see if the wireless problems exist on it. Its fine with gutsy, but it could just be the ipw2200 being nice :) 

At the moment, I believe its the iwlwifi driver, and the madwifi driver... though it could just as easily be wpa_supplicant. My lecturer who has an MBP(with an atheros chipset I believe), uses debian, and hasn't had much luck with the uni wireless for about 3 years.

Annoying thing is, if it just never worked, its atleast something to go by.... thing I dont understand is why it only works sometimes.

---

### Post by kevdog on 2008-05-08
Good luck in HH, Ive yet to upgrade -- the wireless support in the kernel is really bad.  Its a step backwards in my opinion.  Let me know if you get it too work.  The beast right now is a little bit more than I can get a hold on.  A bunch of crappy workarounds are published everywhere.

---

### Post by ThinkDave on 2008-05-10
lexxonnet: Are you using suspend or hibernate? I find that if i use suspend networking restarts as normal and works fine but then drops out intermittently and only resolves itself with a fresh restart.

---

### Post by lexxonnet on 2008-05-10
> **ThinkDave said:**
> lexxonnet: Are you using suspend or hibernate? I find that if i use suspend networking restarts as normal and works fine but then drops out intermittently and only resolves itself with a fresh restart.

I've noticed that as well. However, when I connect at the uni, it does it regardless of whether its a fresh boot or a suspended session.

In fact, if I suspend, it stops associating with the uni network, though it still works with my WPA-PSK network at home.

---

