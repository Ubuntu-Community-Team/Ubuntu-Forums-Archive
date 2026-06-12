---
title: "pa_supplicant won't associate with 3Com Wireless Gateway"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by digmike on 2007-04-24
Hi,

Not sure why I can't authenticate with the 3Com OfficeConnect Wireless 11g Cable/DSL Gateway (3CRWE554G72) we have at work. I'm using wpa_supplicant and the ipw3945 driver, which connects just fine to my Linksys WRT54G wireless router at home.

The 3Com Gateway's admin panel provided me with this information:

3C Number: 3CRWE554G72
Software Version: v1.02.13
Bootload Version: v1.00.00
Wireless Version: v1.0.0.0
Hardware Version: R01A

WPA Encryption: Enabled
WEP Encryption: Disabled
Channel: 11

I have been given the pre-shared key and told the authentication algorithm is TKIP. Below is my wpa_supplicant.conf:

```
update_config=1
# The below line not be changed otherwise we refuse to work
ctrl_interface=/var/run/wpa_supplicant

# Ensure that only root can read the WPA configuration
ctrl_interface_group=wheel

# Let wpa_supplicant take care of scanning and AP selection
ap_scan=1

network={
  ssid="home-wireless"
  psk="home_passphrase"
  priority=5
}

network={
  ssid="work-wireless"
  #key_mgmt=WPA-PSK
  #proto=WPA
  #pairwise=TKIP
  #group=TKIP
  psk=64-bit hex key
  #psk="text_passphrase"
  priority=8
}
```

In the second network block you can see the commented variables I have tried in the past.

wpa_cli shows me this perpetual loop:

```
<2>Trying to associate with 00:0b:ac:e7:ae:ee (SSID='work-wireless' freq=2462 MHz)
<2>Associated with 00:0b:ac:e7:ae:ee
<2>Authentication with 00:0b:ac:e7:ae:ee timed out.
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with 00:0b:ac:e7:ae:ee (SSID='work-wireless' freq=2462 MHz)
<2>Associated with 00:0b:ac:e7:ae:ee
<2>Authentication with 00:0b:ac:e7:ae:ee timed out.
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

So it associates but doesn't authenticate?

Thanks in advance!

---

