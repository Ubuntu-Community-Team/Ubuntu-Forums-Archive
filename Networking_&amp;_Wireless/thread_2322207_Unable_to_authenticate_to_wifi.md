---
title: "Unable to authenticate to wifi"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by edgreenberg on 2016-04-26
So I'm sitting in a campground with wifi, and I can't authenticate.  I can authenticate with my phone just fine. 

Lubuntu 14.04 LTS on a Dell D610.   
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I checked the WPA password several times, carefully.  As I said, the phone can authenticate first try.

Logfiles say

```
Apr 26 20:47:37 cho NetworkManager[777]: <info> NetworkManager state is now CONNECTING
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 20:47:37 cho NetworkManager[777]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0/wireless): connection 'KOA Repeater 1' has security, and se
crets exist.  No new secrets needed.
Apr 26 20:47:37 cho NetworkManager[777]: <info> Config: added 'ssid' value 'KOA Repeater 1'
Apr 26 20:47:37 cho NetworkManager[777]: <info> Config: added 'scan_ssid' value '1'
Apr 26 20:47:37 cho NetworkManager[777]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 20:47:37 cho NetworkManager[777]: <info> Config: added 'psk' value '<omitted>'
Apr 26 20:47:37 cho NetworkManager[777]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 20:47:37 cho NetworkManager[777]: <info> Config: set interface ap_scan to 1
Apr 26 20:47:38 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 26 20:47:38 cho wpa_supplicant[934]: message repeated 9 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 26 20:47:39 cho wpa_supplicant[934]: wlan0: SME: Trying to authenticate with ac:86:74:18:9a:fa (SSID='KOA Repeater 1' fre
q=2437 MHz)
Apr 26 20:47:39 cho kernel: [  984.924253] wlan0: authenticate with ac:86:74:18:9a:fa
Apr 26 20:47:39 cho kernel: [  984.932487] wlan0: send auth to ac:86:74:18:9a:fa (try 1/3)
Apr 26 20:47:39 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 20:47:39 cho kernel: [  985.136185] wlan0: send auth to ac:86:74:18:9a:fa (try 2/3)
Apr 26 20:47:39 cho wpa_supplicant[934]: wlan0: Trying to associate with ac:86:74:18:9a:fa (SSID='KOA Repeater 1' freq=2437 MHz)
Apr 26 20:47:39 cho kernel: [  985.140361] wlan0: authenticated
Apr 26 20:47:39 cho kernel: [  985.144065] wlan0: associate with ac:86:74:18:9a:fa (try 1/3)
Apr 26 20:47:39 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 26 20:47:39 cho kernel: [  985.348181] wlan0: associate with ac:86:74:18:9a:fa (try 2/3)
Apr 26 20:47:39 cho kernel: [  985.552189] wlan0: associate with ac:86:74:18:9a:fa (try 3/3)
Apr 26 20:47:40 cho wpa_supplicant[934]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="KOA Repeater 1" auth_failures=1 duration=10
Apr 26 20:47:40 cho kernel: [  985.756175] wlan0: association with ac:86:74:18:9a:fa timed out
Apr 26 20:47:40 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 26 20:47:50 cho wpa_supplicant[934]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 26 20:47:50 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 26 20:47:51 cho wpa_supplicant[934]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="KOA Repeater 1"
Apr 26 20:47:51 cho wpa_supplicant[934]: wlan0: SME: Trying to authenticate with ac:86:74:18:9a:fa (SSID='KOA Repeater 1' freq=2437 MHz)
Apr 26 20:47:51 cho kernel: [  996.923468] wlan0: authenticate with ac:86:74:18:9a:fa
Apr 26 20:47:51 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 20:47:51 cho kernel: [  996.932409] wlan0: direct probe to ac:86:74:18:9a:fa (try 1/3)
Apr 26 20:47:51 cho kernel: [  997.136181] wlan0: direct probe to ac:86:74:18:9a:fa (try 2/3)
Apr 26 20:47:51 cho kernel: [  997.340178] wlan0: direct probe to ac:86:74:18:9a:fa (try 3/3)
Apr 26 20:47:51 cho wpa_supplicant[934]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="KOA Repeater 1" auth_failures=2 duration=20
Apr 26 20:47:51 cho kernel: [  997.544176] wlan0: authentication with ac:86:74:18:9a:fa timed out
Apr 26 20:47:51 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 26 20:48:01 cho wpa_supplicant[934]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 26 20:48:01 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 26 20:48:03 cho NetworkManager[777]: <warn> Activation (wlan0/wireless): association took too long.
Apr 26 20:48:03 cho NetworkManager[777]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 26 20:48:03 cho NetworkManager[777]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 26 20:48:03 cho NetworkManager[777]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 26 20:48:03 cho NetworkManager[777]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 26 20:48:07 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: scanning -> inactive
Apr 26 20:50:03 cho NetworkManager[777]: <warn> No agents were available for this request.
Apr 26 20:50:03 cho NetworkManager[777]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 26 20:50:03 cho NetworkManager[777]: <info> NetworkManager state is now DISCONNECTED

```

I then created a hotspot in my phone, connecting to my mobile data, and that authenticated fine. 

Can somebody read this and educate me as to what is going on?  I note that there is a section that says:

```
Apr 26 20:47:39 cho kernel: [  985.140361] wlan0: authenticated
Apr 26 20:47:39 cho kernel: [  985.144065] wlan0: associate with ac:86:74:18:9a:fa (try 1/3)
Apr 26 20:47:39 cho NetworkManager[777]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 26 20:47:39 cho kernel: [  985.348181] wlan0: associate with ac:86:74:18:9a:fa (try 2/3)
Apr 26 20:47:39 cho kernel: [  985.552189] wlan0: associate with ac:86:74:18:9a:fa (try 3/3)
Apr 26 20:47:40 cho wpa_supplicant[934]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="KOA Repeater 1" auth_failures=1 duration=10
Apr 26 20:47:40 cho kernel: [  985.756175] wlan0: association with ac:86:74:18:9a:fa timed out

```
So it says "authenticated" but then fails in "associating."  

I'll be here a few more days, and wonder if I can resolve this. 

Thanks 

Ed G

---

### Post by DuckHook on 2016-04-26
I've moved your post to the Networking & Wireless forum where you will get more relevant help. I've also wrapped your output in code tags for easier reading. Please use them from now on when posting code.

---

### Post by jeremy31 on 2016-04-27
It might be the spaces in the wifi SSID causing the problem

---

