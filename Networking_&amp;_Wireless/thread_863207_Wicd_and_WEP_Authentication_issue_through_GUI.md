---
title: "Wicd and WEP Authentication issue through GUI"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by iletumi on 2008-07-18
Hello everyone, 

I have spent a fair share of time now trying to troubleshoot a specific issue i can not seem to resolve through multiple sources on these forums and abroad. 

Currently i am running Hardy on my laptop (ML6720). It was a challenge setting up wireless on this laptop as many of you may know. 

At my current state of the problem i have confirmed that my wireless is working properly to an extent. 

At home i use an Open WEP key 128-bit. 
At work i use a Shared WEP key 128-bit. 

I use Wicd for management and i have come across of few issues. I have tried all possible options (HEX & Passphase) but to no resolve Wicd stops at  none: obtaining ip address. 

The only way i can get connected is to enter the Wep key in CLI during the *"Essid: Obtaining IP Address. *  portion of the wicd connection process. 

At home it works if i enter: **sudo iwconfig wlan0 key xxxxxxxxxxxxxxxxxxxxxxxxxx**

At work it works if i enter: **sudo iwconfig wlan0 key open xxxxxxxxxxxxxxxxxxxxxxxxxx**

Once i enter the key it authenticates from  "none: obtaining ip address" to the proper AP essid and grabs a dhcp address and connects.

(also if anyone knows the command for Wicd to startup at boot through Session options that would be great!)   I am currently entering /opt/wicd/tray.py


Thank you to anyone who can help.


p.s. i am very reluctant to ask for help with out exhausting all other options first

---

### Post by imdano on 2008-07-18
This is a frustrating issue I've seen a few others have.  For some reason wpa_supplicant isn't able to authenticate the WEP connection, but using iwconfig works.  I don't have the problem on my box so I haven't been able to try to figure out why.

If you're comfortable running wpa_supplicant manually, it'd be helpful if you could post the output of:
```
wpa_supplicant -i <wireless interface> -c /opt/wicd/encryption/configurations/<your AP bssid> -D wext -d
```You can increase the debugging verbosity by adding more 'd''s to the end. (-dd, -ddd).

If you add the command /opt/wicd/tray.py to Sessions if should start up at boot.

---

### Post by iletumi on 2008-07-19
Initializing interface 'wlan0' conf '/opt/wicd/encryption/configurations/TDCMAP2' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/opt/wicd/encryption/configurations/TDCMAP2' -> '/opt/wicd/encryption/configurations/TDCMAP2'
Reading configuration file '/opt/wicd/encryption/configurations/TDCMAP2'
Failed to read or parse configuration '/opt/wicd/encryption/configurations/TDCMAP2'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

Thats the output, i do believe that Wicd is set to use ndiswrapper for the wpa supplicant driver when i select wext i get the same results.

Also i do have the /opt/wicd/tray.py set in sessions with no luck. It may just seem that it does not load due to the authentication issue with auto connection.

---

### Post by imdano on 2008-07-19
I think you misunderstood.  The file '/opt/wicd/encryption/configurations/TDCMAP2' doesn't exist.  You're looking for /opt/wicd/encryption/configurations/<your ap's bssid>.  The bssid is the MAC address, except with all the ':' characters removed.  So if iwconfig lists it as "Access Point: 00:0F:66:31:B9:67", then file full file would be '/opt/wicd/encryption/configurations/000f6631b67'.

---

### Post by iletumi on 2008-07-21
Ah excuse me i did misunderstand here is the proper result.


Initializing interface 'wlan0' conf '/opt/wicd/encryption/configurations/00184D0E2E55' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/opt/wicd/encryption/configurations/00184D0E2E55' -> '/opt/wicd/encryption/configurations/00184D0E2E55'
Reading configuration file '/opt/wicd/encryption/configurations/00184D0E2E55'
Failed to read or parse configuration '/opt/wicd/encryption/configurations/00184D0E2E55'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout


This is the information located within the file

ap_scan=1

network={
       ssid="ESSID"
       scan_ssid=0
       key_mgmt=NONE
       wep_key0=xxxxxxxxxxabcdef9876543210
       wep_tx_keyidx=0
       priority=5
}


removed essid since it is my companies network at this time.  This network requires me to use the OPEN tag in the Wep key entry in command line.

---

### Post by iletumi on 2008-07-21
I also did some testing with the default NetworkManager and i get the same results. I have to enter the key manually at the time of connection or it fails.

---

### Post by imdano on 2008-07-22
Something still isn't quite right with that output, are you sure you gave the right file name to wpa_supplicant (case matters! Hi.txt is not the same as hi.txt)?  The error your getting means wpa_supplicant can't read your config file, which shouldn't happen unless its not finding the file at all.

---

### Post by iletumi on 2008-07-22
Copied directly from Terminal: 

UbuMobile:~$ wpa_supplicant -i wlan0 -c /opt/wicd/encryption/configurations/00184D0E2E55 -D wext -ddd
Initializing interface 'wlan0' conf '/opt/wicd/encryption/configurations/00184D0E2E55' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/opt/wicd/encryption/configurations/00184D0E2E55' -> '/opt/wicd/encryption/configurations/00184D0E2E55'
Reading configuration file '/opt/wicd/encryption/configurations/00184D0E2E55'
Failed to read or parse configuration '/opt/wicd/encryption/configurations/00184D0E2E55'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

I will look into reinstalling wpa supplicant since it seems to be the issue at this point if thats a way of resolving this problem.

Thanks.

---

### Post by imdano on 2008-07-22
Can you paste an ls of /opt/wicd/encryption/configurations?

---

