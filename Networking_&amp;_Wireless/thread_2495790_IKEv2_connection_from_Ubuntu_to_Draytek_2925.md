---
title: "IKEv2 connection from Ubuntu to Draytek 2925"
date: 2024-03-01
forum: Networking &amp; Wireless
---

### Post by andifa on 2024-03-01
Hello everyone,

I just can't figure out how to establish a VPN connection from Ubuntu 22.04 to a Draytek Vigor 2925 router using IKEv2. The router always returns "Prase error : DH group of IKEv2 Key Exchange Payload has an unknown value: 31"

This is my config on the Draytek

[IMG]https://ibb.co/7Q4J9QM[/IMG][IMG]https://i.ibb.co/cwLcmwf/Draytek-General-IPsec-Conf.png[/IMG]
[IMG]https://i.ibb.co/NK6fyCk/VPNUser-Config.png[/IMG]

And on Ubuntu (using strongswan):
[IMG]https://i.ibb.co/YWpZTDN/Ubuntu-VPNconfig1.png[/IMG]


/var/log/syslog
```
Mar  1 08:13:34 Thinkpad-T420s NetworkManager[614]: <info>  [1709277214.6159] vpn[0x557fc18521f0,d030d32c-6e60-4ddf-99b5-8caf22701543,"Company IKEv2"]: starting strongswan
Mar  1 08:13:34 Thinpad-T420s NetworkManager[614]: <info>  [1709277214.6168] audit: op="connection-activate" uuid="d030d32c-6e60-4ddf-99b5-8caf22701543" name="Company IKEv2" pid=6845 uid=1000 result="success"
Mar  1 08:13:42 Thinkpad-T420s charon-nm: 05[CFG] received initiate for NetworkManager connection Company IKEv2
Mar  1 08:13:42 Thinkpad-T420s charon-nm: 05[CFG] using gateway identity 'Nie****'
Mar  1 08:13:42 Thinkpad-T420s charon-nm: 05[IKE] initiating IKE_SA Company IKEv2[2] to 68.x.x.x
Mar  1 08:13:42 Thinkpad-T420s charon-nm: 05[ENC] generating IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) N(FRAG_SUP) N(HASH_ALG) N(REDIR_SUP) ]
Mar  1 08:13:42 Thinkpad-T420s charon-nm: 05[NET] sending packet: from 192.168.178.32[35082] to 68.x.x.x[500] (904 bytes)
Mar  1 08:13:46 Thinkpad-T420s charon-nm: 08[IKE] retransmit 1 of request with message ID 0
Mar  1 08:13:46 Thinkpad-T420s charon-nm: 08[NET] sending packet: from 192.168.178.32[35082] to 68.x.x.x[500] (904 bytes)
Mar  1 08:13:53 Thinkpad-T420s charon-nm: 09[IKE] retransmit 2 of request with message ID 0
Mar  1 08:13:53 Thinkpad-T420s charon-nm: 09[NET] sending packet: from 192.168.178.32[35082] to 68.x.x.x[500] (904 bytes)
Mar  1 08:14:06 Thinkpad-T420s charon-nm: 10[IKE] retransmit 3 of request with message ID 0
Mar  1 08:14:06 Thinkpad-T420s charon-nm: 10[NET] sending packet: from 192.168.178.32[35082] to 68.x.x.x[500] (904 bytes)
Mar  1 08:14:29 Thinkpad-T420s charon-nm: 11[IKE] retransmit 4 of request with message ID 0
Mar  1 08:14:29 Thinkpad-T420s charon-nm: 11[NET] sending packet: from 192.168.178.32[35082] to 68.x.x.x[500] (904 bytes)
Mar  1 08:14:37 Thinkpad-T420s wpa_supplicant[663]: wlp3s0: WPA: Group rekeying completed with 0c:72:74:12:dc:ef [GTK=CCMP]
Mar  1 08:14:42 Thinkpad-T420s NetworkManager[614]: <warn>  [1709277282.7707] vpn[0x557fc18521f0,d030d32c-6e60-4ddf-99b5-8caf22701543,"Company IKEv2"]: connect timeout exceeded
Mar  1 08:14:42 Thinkpad-T420s charon-nm[6798]: Connect timer expired, disconnecting.
Mar  1 08:14:42 Thinkpad-T420s charon-nm: 06[IKE] destroying IKE_SA in state CONNECTING without notification
```

Router syslog (reverse order):
```
"2024-03-01 06:36:31", "## IKEv2 DBG : Process Packet : Parse payload failed"
"2024-03-01 06:36:31", "## IKEv2 DBG : Can't parse IKEv2_NP_v2KE "
"2024-03-01 06:36:31", "Prase error : DH group of IKEv2 Key Exchange Payload has an unknown value: 31 "
"2024-03-01 06:36:31", "## IKEv2 DBG : Recv IKEv2_SA_INIT[34] Request msgid 0 from 2.x.x.x, Peer is IKEv2 Initiator"
```

Any ideas are greatly appreciated.

Best, Andreas

---

### Post by volkswagner on 2024-03-02
I’m not familiar with DrayTek. It looks like you’ve put username in the identity field. Identity would be = remote ID.

The specific error is regarding DH group. I don’t see DH group setting in your client screenshot.

---

### Post by andifa on 2024-03-03
Thanks for the reply. I changed 'Identity' on Ubuntu to the common name of the local certificate.

Sorry, I don't know what a 'DH group' is. Where Do I find this setting?

---

### Post by volkswagner on 2024-03-03
I'm no expert, but I know the settings need to match on both ends.
You need to configure StrongSwan with Diffie Hellman Groups to
be the same value on each side. It looks like your router can't
change the setting from the list of offerings (G21, G20, G19, etc).
Try to configure strongswan to use G21 with AES256 if you can.
[https://docs.strongswan.org/docs/5.9/config/IKEv2CipherSuites.html](https://docs.strongswan.org/docs/5.9/config/IKEv2CipherSuites.html)

I''ve never used the GUI, so I can't say where the settings get changed.
If you can edit /etc/ipsec.conf, you may find more joy.

Here's an example of a portion of my config that would set your DH Group..

```

    ike=aes256-sha512-modp2048
    keyexchange=ikev2
    esp=aes256-sha256-modp2048

```

---

### Post by andifa on 2024-03-05
Sorry, I have read a little bit through the docs but I don't get along. I  don't have /etc/ipsec.conf (deprecated according to docs?). What I see  is /etc/strongswan.conf which loads everything in  /etc/strongswan.d/charon/ and /etc/swanctl.conf (the latter is empty). Can  I put your configuration anywhere there?

---

### Post by volkswagner on 2024-03-05
It's hard to say. I never used the gui. When you make changes in the gui, do you
see them reflected in the config files?
Can you post the contents of the config file and protect private items
like public IP and passwords?

---

### Post by andifa on 2024-03-08
This is the config file in /etc/NetworkManager/system-connections/VPN/

```
[connection]
id=VPN
uuid=d4155fe7-xxxx
type=vpn
autoconnect=false
permissions=user:andreas:;

[vpn]
address=x.x.x.x
encap=no
ipcomp=no
local-identity=x.x.x.x
method=psk
password-flags=2
proposal=no
virtual=no
service-type=org.freedesktop.NetworkManager.strongswan

[ipv4]
method=auto

[ipv6]
addr-gen-mode=stable-privacy
method=auto

[proxy]
```

---

### Post by volkswagner on 2024-03-08
I'm sure sure I'm much help here. I'm just guessing.

Perhaps try adding (inside the [vpn] section):

```

    ike=aes256-sha256-modp2048
    esp=aes256-sha256-modp2048

```

to your config file, then check logs for any changes.
You can also try adding one line at a time.
modp2048 should be compatible with G14 listed on the router.

---

