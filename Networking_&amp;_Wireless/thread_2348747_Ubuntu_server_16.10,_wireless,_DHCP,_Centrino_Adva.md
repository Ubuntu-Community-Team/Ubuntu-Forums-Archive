---
title: "Ubuntu server 16.10, wireless, DHCP, Centrino Advanced-N 6200 = no go"
date: 2017-01-06
forum: Networking &amp; Wireless
---

### Post by nraygun on 2017-01-06
(Could swear I posted this earlier.)

I loaded Ubuntu server 16.10 on a Dell E6410 laptop. I found that the adapter is called wlp2s0 and edited the /etc/networks/interfaces file as follows.
It tries to DHCP, but then fails.

The wireless worked during the installation of the OS.

Any ideas?

auto wlp2s0
iface wlp2s0 inet dhcp
wpa-ssid Blah
wpa-psk blahblah123

---

### Post by nraygun on 2017-01-06
This always happens - I got it! Right after I sent the post, I tried the other method of using the wpa-supplicant from the link below and it worked.
It also booted to using the wireless adapter.
[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

And the method I used from the article:

[COLOR=#111111][FONT=Ubuntu]Using either DHCP or a static config (doesn't matter which)--AND assuming your wifi worked during install--make your **/etc/network/interfaces** look something like below (for **wlan0** should match the name of your wifi card listed under **ifconfig -a** e.g. your detected wifi card could be nicknamed **eth1** by the OS for all I know.):[/FONT][/COLOR]
 auto lo iface lo inet loopback     
 auto wlan0 iface wlan0 inet dhcp    
 wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
[COLOR=#111111][FONT=Ubuntu]To configure wpa_supplicant use the command (Referenced in the config above)[/FONT][/COLOR]
wpa_passphrase "YOUR_SSID" SSID_PASSWORD | sudo tee /etc/wpa_supplicant/wpa_supplicant.conf
[COLOR=#111111][FONT=Ubuntu]Next, create a new executable script named **iwconfig** (you can name this script anything really, "iwconfig-default-ssid", perhaps?--I just made it short for the example):[/FONT][/COLOR]
sudo touch /etc/network/if-up.d/iwconfig && sudo chmod 700
/etc/network/if-up.d/iwconfig && sudo ln -s
/etc/network/if-up.d/iwconfig /etc/network/if-pre-up.d/iwconfig
[COLOR=#111111][FONT=Ubuntu]Now edit **/etc/network/if-up.d/iwconfig** and add the SSID you want Ubuntu Server to connect to on startup:[/FONT][/COLOR]
#!/bin/sh
iwconfig wlan0 essid "YOUR_DEFAULT_SSID" mode managed
[COLOR=#111111][FONT=Ubuntu]Now bring ifdown (if you haven't already), then ifup, and you should be golden now and when you reboot (as long as you're near your SSID.)[/FONT][/COLOR]

---

