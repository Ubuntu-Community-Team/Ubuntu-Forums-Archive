---
title: "WPA2 password problem"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Bloodspike on 2008-02-11
I'm having a problem entering my WPA2 passphrase in wpa_supplicant.  I am using a website that generates strings of 63 random printable ASCII character to use as phassphrases.  For example:

``u]!;!orfB"2%-El+ma[q@yYN@~%>H%F+&r~5]/*,1OkKKU@Rn_VKN(vv!sQ>\)

I am using a similiar passphrase for all of my windows computers without problems, can I use this phrase in Ubuntu?

wpa_passphrase chokes on the string so I manually converted it to hex and entered it into wpa_supplicant.conf.  To see what was happening when I started wpa_supplicant I executed 

sudo wpa_supplicant -w -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd

and got the following resuts:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     6d 61 6e 64 6d                                    mandm           
scan_ssid=1 (0x1)
key_mgmt: 0x8
pairwise: 0x18
group: 0x18
Line 10: Invalid PSK '<passphrase>'.
Line 10: failed to parse psk '<passphrase>'.
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout


I really dont want to use a less secure alphanumeric passphrase for my WPA2 key, can anyone suggest something?


Thanks

---

### Post by wieman01 on 2008-02-12
Random keys can be a problem, but if you avoid any sort of apostrophes (e.g. ', ", `) you should be OK. Just remove or replace them.

Second, you cannot generate a passphrase manually as a passphrase is more than just your personal key in hexadecimal format. I believe it is the encrypted version of your password, so you have to invoke "wpa_passphrase" in order for your system to work.

Does that help?

---

