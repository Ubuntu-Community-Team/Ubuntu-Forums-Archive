---
title: "Hostapd not working after dist upgrade from ubuntu server 16 to 18.04"
date: 2018-11-26
forum: Networking &amp; Wireless
---

### Post by vk6pal on 2018-11-26
Hi

I did a Dist upgrade from Ubuntu server 16.x to 18.04 and hostapd is now not working. The following is the Error message are;

[TABLE="class: outer_border, width: 1500"]
[TR]
[TD]shaun@router:~$ sudo systemctl status hostapd
&#9679; hostapd.service - Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
   Loaded: loaded (/lib/systemd/system/hostapd.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-11-25 18:04:33 AWST; 23h ago
  Process: 7488 ExecStart=/usr/sbin/hostapd -P /run/hostapd.pid -B $DAEMON_OPTS ${DAEMON_CONF} (code=exited, status=1/FAILURE)

Nov 25 18:04:33 router hostapd[7488]: HT (IEEE 802.11n) with WPA/WPA2 requires CCMP/GCMP to be enabled, disabling HT capabilities
Nov 25 18:04:33 router hostapd[7488]: nl80211: Could not configure driver mode
Nov 25 18:04:33 router hostapd[7488]: nl80211: deinit ifname=wlp3s0 disabled_11b_rates=0
Nov 25 18:04:33 router hostapd[7488]: nl80211 driver initialization failed.
Nov 25 18:04:33 router hostapd[7488]: wlp3s0: interface state UNINITIALIZED->DISABLED
Nov 25 18:04:33 router hostapd[7488]: wlp3s0: AP-DISABLED
Nov 25 18:04:33 router hostapd[7488]: hostapd_free_hapd_data: Interface wlp3s0 wasn't started
Nov 25 18:04:33 router systemd[1]: hostapd.service: Control process exited, code=exited status=1
Nov 25 18:04:33 router systemd[1]: hostapd.service: Failed with result 'exit-code'.
Nov 25 18:04:33 router systemd[1]: Failed to start Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator.

[/TD]
[/TR]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

and this error message when i run journalctl -xe
[TABLE="class: outer_border, width: 1500"]
[TR]
[TD]shaun@router:~$ journalctl -xe
-- Unit hostapd.service has begun starting up.
Nov 26 17:57:33 router hostapd[8957]: Configuration file: /etc/hostapd/hostapd.conf
Nov 26 17:57:33 router hostapd[8957]: HT (IEEE 802.11n) with WPA/WPA2 requires CCMP/GCMP to be enabled, disabling HT capabilities
Nov 26 17:57:33 router hostapd[8957]: nl80211: Could not configure driver mode
Nov 26 17:57:33 router hostapd[8957]: nl80211: deinit ifname=wlp3s0 disabled_11b_rates=0
Nov 26 17:57:33 router hostapd[8957]: nl80211 driver initialization failed.
Nov 26 17:57:33 router hostapd[8957]: wlp3s0: interface state UNINITIALIZED->DISABLED
Nov 26 17:57:33 router hostapd[8957]: wlp3s0: AP-DISABLED
Nov 26 17:57:33 router hostapd[8957]: hostapd_free_hapd_data: Interface wlp3s0 wasn't started
Nov 26 17:57:33 router systemd[1]: hostapd.service: Control process exited, code=exited status=1
Nov 26 17:57:33 router systemd[1]: hostapd.service: Failed with result 'exit-code'.
Nov 26 17:57:33 router systemd[1]: Failed to start Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator.
-- Subject: Unit hostapd.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit hostapd.service has failed.
--
-- The result is RESULT.
Nov 26 17:57:33 router sudo[8946]: pam_unix(sudo:session): session closed for user root
Nov 26 17:58:02 router dhcpd[7056]: Wrote 11 leases to leases file.
Nov 26 17:58:02 router dhcpd[7056]: DHCPREQUEST for 10.1.1.11 from 4c:ed:fb:67:34:0f (DESKTOP-B4OC732) via enp4s0
Nov 26 17:58:02 router dhcpd[7056]: DHCPACK on 10.1.1.11 to 4c:ed:fb:67:34:0f (DESKTOP-B4OC732) via enp4s0

[/TD]
[/TR]
[/TABLE]

The following is my hostapd.conf

[TABLE="width: 1500"]
[TR]
[TD]# /etc/hostapd/hostapd.conf

# The interface to run the access point on
interface=wlp3s0

# The wireless network name
ssid=Shaun_Wireless

# Sets up the regulatory domain of the network. This sets
# up things like available channels, transmit power, etc.
# based on the country the network is operating in.
country_code=US

# Enable IEEE 802.11d which actually enforces the policies
# mandated by the country_code.
ieee80211d=1

# WiFi mode to use (a, b or g). The g mode does n too, don't
# panic.
hw_mode=g

# Enable n mode as well.
ieee80211n=1

# The wireless channel to use. Use a WiFi scanner app on
# your phone to find a channel without to much interference
# and choose that one.
channel=7

# Some sort of protocol detail. I dunno, you just need it.
wmm_enabled=1

# Use shared key authentication
auth_algs=1

# ignore_broadcast_ssid=1

# Enable WPA2 for authentication and configure the key
# management and encryption types.
wpa=2
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
rsn_pairwise=TKIP

# Set the password for the network
wpa_passphrase=password

[/TD]
[/TR]
[/TABLE]

Is any able to help  Not sure where to start

Regard

shaun

---

