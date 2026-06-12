---
title: "Protected management frames required on AP - how to connect to it?"
date: 2018-01-25
forum: Networking &amp; Wireless
---

### Post by zeehaa on 2018-01-25
I'd like to connect to a wifi router which requires "protected management frames". 
My android mobile can use it without any problems.
I'm using Ubuntu 16.04.3 on my laptop, and it can't connect to that router. In network-manager it's names is greyed out.
In wpa_supplicant, pmf is set to 0. (which means: no protected management frames)
Is there any way to enable it?
There is no wpa_supplicant.conf, if I create one in /etc, the automatically started wpa_supplicant ignores it.
The network-manager package in Ubuntu 16.04 is too old (1.2.6), only the latest (1.10.2) knows pmf...
Any idea?

---

### Post by zeehaa on 2018-01-27
For the posterity...
Because there is no support for protected frames in the built in versions of network-manager, it must be disabled to use PMF. 
The simplest way to do it is put wireless interface into /etc/network/interfaces:
[FONT=courier new][B]iface wlp1s0 inet dhcp
   wpa-conf /etc/wpa_supplicant.conf
[/B][/FONT]
and then put something like this to /etc/wpa_supplicant.conf:
[FONT=courier new][B]
ctrl_interface=DIR=/run/wpa_supplicant GROUP=adm
update_config=1

network={
    ssid="My_Router"
    scan_ssid=1
    key_mgmt=WPA-PSK-SHA256
    psk="pre-shared-key"
    ieee80211w=2
[/B][/FONT][B]}

pmf=2
[/B]
If you've done this, restart network-manager, and start wireless with "ipup wlp1s0".

---

