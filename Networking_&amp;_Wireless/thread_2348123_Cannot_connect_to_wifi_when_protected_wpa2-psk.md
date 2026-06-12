---
title: "Cannot connect to wifi when protected wpa2-psk"
date: 2016-12-31
forum: Networking &amp; Wireless
---

### Post by axlor on 2016-12-31
First, let me get you up to speed on where I am...

I am using a Netgear WNA3100 usb device which requires me to use ndiswrapper for its drivers. No, problem.
I can detect networks using any number of services. Network Manager, wifi-radar, wicd, they all can scan just find and detect networks I can connect to.

Currently the network manager (thing in the top right) can detect my wireless network (as well as a neighbor's) but when attempting to connect it prompts me for a password, does some thinking, then prompts me for a password again. This repeats indefinitely. I know I have the right password. Some other information provided in the imgur link.

[http://i.imgur.com/7OmIsrF.jpg](http://i.imgur.com/7OmIsrF.jpg)

Also, I'm using a NETGEAR wnr2000v3 router. The logs are showing that the device is being assigned a local dhcp ip (mac address is correct), but wlan access is being denied for incorrect security.

[DHCP IP: 192.168.1.6] to MAC address 4c:.....etc    
[WLAN access rejected: incorrect security] from MAC address 4c:......etc

I've double checked the network manager settings several times, I know it is set to WPA2-PSK [AES] (personal). I also know I'm entering the password correctly. 
-------------------------------------
I've set up a guest network with no security and am able to connect to that network and access the internet no problem, so it has to be something with wpa_supplicant right? It looked to me like wicd, network manager, etc all use wpa_supplicant when wpa/wpa2 are in use.

Another thing I've tried doing is running wpa_supplicant using: sudo wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=1
```

Then using wpa_cli, scanning in wpa_cli shows the network I want to connect to. Then using the WPS feature: wps_pbc. I click the WPS button on my router and wpa_cli sees this and attempts to setup a connection but fails with the following:

<3>WPS-AP-AVAILABLE-PBC 
<3>Trying to associate with 84:1b:5e:69:fb:34 (SSID='NETGEAR03' freq=2412 MHz)
<3>Authentication with 84:1b:5e:69:fb:34 timed out.
<3>CTRL-EVENT-DISCONNECTED bssid=84:1b:5e:69:fb:34 reason=3 locally_generated=1

I really don't know what could be wrong. I feel like I've narrowed it down to something that has to do with the encryption/security protocols but I know my password is correct and everything I've tried has failed, including the WPS method which should set everything automatically right?
Any ideas would be appreciated.
------------------------------------------------------

ps: side note. Something was renaming wlan0 to enx<Mac Address>. I changed it so the interface remains named to wlan0 since I thought that may have been an issue but it didn't change anything.

---

### Post by ajgreeny on 2017-01-01
I think what is wrong is that you have a Netgear WNA3100 which is well known to be very problematical in Linux.

You can keep trying but I fear you may find that the simplest solutiojn is to bite the bullet and get hold of another wifi adapter which is known to work out of the box with Ubuntu.

I will unfortunately have to leave you to search for yourself as my wifi knowledge is very scant and I have never had any problems with my own wifi hardware.

---

### Post by axlor on 2017-01-01
my wna3100 connect to the internet though without issue on ubuntu when it isn't wpa protected. I don't see how the wireless adapter could be the issue.

---

### Post by ajgreeny on 2017-01-02
I agree in general terms, and you may have luck using other router security, but is that an acceptable answe4 for you?
WPA2 is the only sensible way to protect a wifi network and even if you change your own router settings most others that you try to connect to will be WPA2 and therefore unavailable to you.

Have you looked into using ndiswrapper which in the past has occasionally been of use with difficult Netgear adapters?

---

