---
title: "FreedomNetv2 on Ubuntu?"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by serlex on 2006-10-23
Can not connect to university's wireless net. I asked within the uni for this, but not luck. Looks like they have a clue how to run it on Linux.

My wireless works fine at home on my normal router.

Here some instructions by the university:
```
The first stage is to convert the UOP certificate that's email to you in to a format that can be used under Linux:
# openssl x509 -out UOP-b64.cer -inform DER -outform PEM < UOP.cer

The above command will create you a file called UOP-b64.cer which you should be able to view (using cat for example).

The next stage is to install and configure the program that will connect you to the wireless network. For this we'll be using wpa_supplicant. Your distribution may package this for you or you can download and build it yourself.

1.) Install wpa_supplicant.
2.) Copy the UOP-b64.cer file somewhere on your Linux install (to your $HOME for example, or /opt).
3.) Create/edit your wpa_supplicant.conf file (usually located in /etc). The network block for the University wireless should look like the following:
Code:

network={
        ssid="FreedomNetv2"
        mode=0
        proto=WPA
        key_mgmt=WPA-EAP
        eap=TTLS
        pairwise=TKIP
        group=TKIP
        identity="ece99999"
        password="yourpassword"
        ca_cert="/opt/UOP-b64.cer"
        phase2="auth=PAP"
        priority=2
}

4.) Save the file and you're all set!

You can set the ap_scan option in wpa_supplicant.conf to either 1 or 2. Either should work but I would recommend setting it to 2 (ap_scan=2).

Test it by running (as root):
# wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D wext -ddd
(Obviously replace eth1 with your wireless interface etc.)

```

I followed and completed each step, still not luck
Wireless card:2200BG

any ideas?

---

### Post by serlex on 2006-10-23
bump!

---

