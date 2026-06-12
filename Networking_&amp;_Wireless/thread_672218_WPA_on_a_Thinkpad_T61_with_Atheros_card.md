---
title: "WPA on a Thinkpad T61 with Atheros card"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by lunatico on 2008-01-19
So this is the problem I'm having:
I have a Thinkpad T61 with a 5212 Atheros wireless card.
Ubuntu loads the drivers and it loads madwifi. It works well with open wireless networks.
In my university the wireless network uses WPA-Enterprise/TKIP/PEAP.
I have not been able to configure wpa_supplicant to connect.

I have done a lot of research and as far as I know there are two ways to configure this. Using the /etc/network/interfaces file and also the wpa_supplicant.conf None of these have worked for me.

The outcome of the scan on the wireless network is:
          Cell 04 - Address: 00:1D:A2:0F:1C:20
                    ESSID:"COMPSCIwireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : none TKIP
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101820003a4000027a4000042435e0062322f00

The wpa_supplicant commands I think I need are:
network={
	ssid="COMPSCIwireless"
	scan_ssid=1
	key_mgmt=WPA-EAP
	pairwise=TKIP
	group=TKIP
	eap=PEAP
	identity="user"
	password="password"
}


It will not work. I am no expert so I hope anyone can help me or guide me on how to fix it.

Thank you!

---

### Post by lunatico on 2008-02-10
I got this sorted. Ask if someone need help.

---

### Post by canclan on 2008-03-01
Hello!
May I ask what you ended up doing?
Thanks!

---

### Post by lunatico on 2008-03-01
Sure. I really don't have a good explanation to why what I did works but it does. I think that I played a lot with settings and stuff... I'm planning to make a fresh installation of the whole OS soon just to make sure of what I need and stuff... but for now here is what I did to fix this.
First make sure you have installed wpa_supplicant and your wifi drivers. It is also good if you could test your wireless card on an open network. If that works then go ahead and install WICD. This will uninstall NetworkManager, so from there on you use that GUI for network settings, which in my opinion is a very good one.

Then when I want to connect to my college wireless network what I do is:
1. From WICD I hit disconnect. Even if you think you have not connected, do it.
2. From command line run the wireless connection script which in my case is a file with execute permissions that runs this command: wpa_supplicant -dd -i <your_wifi_interface> -c <path_to_your_wpawupplicant_config_file> -D madwifi

My wpa supplicant config file looks like:
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="<your_ssid>"
        scan_ssid=1
        key_mgmt=WPA-EAP
        mode=0
        eap=LEAP
        identity="<username>"
        password="<password>"
}

You will see a lot of stuff when running this, once you see three consecutive lines saying something about eapol.... (I don't remember, if you need it remind me during the week) that means that the auth process was done and you are authenticated in the network.
On a different terminal window check if you got the proper ip address, if not just do a sudo dhclient <network_interface>
This should do the trick.
Is this clear?

---

### Post by canclan on 2008-03-03
Thanks for the reply!  I will see if I can get a few minutes to try it this week.  I will let you know how it goes when I give it a try.

canclan.

---

