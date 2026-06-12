---
title: "wpa_supplicant and pre-authentication"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by nidiel on 2006-12-19
Hello
I'm using wpa_supplicant v0.4.9 with the following configuration file:
network={
        ssid="my_essid"
        key_mgmt=WPA-EAP
        proactive_key_caching=1
        eap=TTLS
        identity="my_id"
        anonymous_identity="anonymous"
        password="my_pw"
        ca_cert="my_certificate.crt"
}

My configuration is as following:
2 Access Points (AP_1 and AP_2) with same essid that request radius authentication.
Both APs support WPA2.
I have also a wire and wireless sniffer (ethereal).

The supplicant is associated and radius authenticated with AP_1.
Using wpa_cli I initiate a pre-authentication (>preauth <AP_2 BSSID>).

The AP_2 receive through wire via AP_1 from supplicant EAPOL START message and answer with EAP Request Identity.

On the wireless sniffer I can see the EAP Request Identity is sent to supplicant.

After that I expect the suplicant to continue the radius authentication process but insteed of that, it send EAPOL START to the AP is il already associated (AP_1) and ignore the EAP Request Identity.
After a timeout the suppicant send an EAPOL START message to AP_2 again.

I don't understand why the supplicant ignore the EAP Request Identity message and why it send an EAPOL START to the AP it is already associated and authenticated with.

Somebody can help me ?

Thanks

---

