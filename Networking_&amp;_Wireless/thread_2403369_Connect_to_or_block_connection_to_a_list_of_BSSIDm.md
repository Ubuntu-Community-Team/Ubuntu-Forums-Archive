---
title: "Connect to or block connection to a list of BSSID/mac addresses"
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by dillonregi on 2018-10-10
I'm trying to control how my laptop "roams" between various access points of the same SSID, as I'm having issues when using specific ones (something to do with how their firewalls are configured, which is out of my control).
 I have a list of known good, and a list of known bad BSSIDs and mac addresses.
Currently I'm manually selecting a working AP through the network manager each time I move out of range, but it is tedious to do so each time I move my laptop to a new room.

Is there a configuration file somewhere which I'm able to enter a list of specific devices/APs/BSSIDs/mac addresses that my laptop is allowed to connect to, or that are blocked? There's about 30 on each list of working/not working.


Network controller: Intel Corporation Wireless 7265 (rev 59)
Ubuntu 18.04.1 LTS

EDIT: The options in wpa_cli allow blacklisting BSSID's
```
$ wpa_cli help | grep "blacklist <BSSID>" -b1
bssid <network id> <BSSID> = set preferred BSSID for an SSID
blacklist <BSSID> = add a BSSID to the blacklist
blacklist clear = clear the blacklist
```

---

### Post by QIII on 2018-10-10
Hello!

It might be helpful if you would describe to us to what end you are seeking to do this.

Thanks!

---

### Post by dillonregi on 2018-10-11
> **QIII said:**
> Hello!

It might be helpful if you would describe to us to what end you are seeking to do this.

Thanks!

I'm hoping that I can make my laptop connect to one of a specific list of APs at my place of work as my laptop's WiFi roams. I want to exclude specific APs that broadcast the same SSID.

As an example (but not exactly what's going on in my case), imagine the following:
You have a WiFi mesh network consisting of 3 routers all configured with the SSID "MyWiFi" and a password of "password".
 Your neighbour also has a couple routers configured the same, with the SSID "MyWiFi" and password "password". 
Any time you bring your laptop outside and are thus closer to your neighbours house, your laptop connects to your neighbours router.
Their router accepts the connection, but doesn't have a line to the internet, so you aren't able to access your emails.
Also, you and your neighbour are both unable to change any of the router/AP settings

---

### Post by him610 on 2018-10-13
> you and your neighbour are both unable to change any of the router/AP settings
Is this because you do not have access to the router/AP or because technical skills are lacking?
You may uniquely identify your own network by setting the BSSID = AP MAC address in your Network Configurations file. The MAC address of your router/AP can be located on a sticker attached to the back, bottom, or side of the device, or the box it came in. It may read *MAC ID* or *MAC Address* followed by twelve hexadecimal numbers.

Here is a good explanation of SSID & BSSID. [https://www.juniper.net/documentation/en_US/junos-space-apps/network-director2.0/topics/concept/wireless-ssid-bssid-essid.html]("https://www.juniper.net/documentation/en_US/junos-space-apps/network-director2.0/topics/concept/wireless-ssid-bssid-essid.html")

---

### Post by dillonregi on 2018-10-13
I don't have access to the router config because this is at my place of work. The "neighbour" thing was just an example, all of the routers are on the same network (just some have different configurations)

I do have some small networking knowledge, and a list of the MAC addresses and BSSIDs of the routers that I would like to connect to. I'm just not sure if it's possible to use that list to control which APs my laptop connects to (and in turn, which ones it will avoid)

---

### Post by QIII on 2018-10-15
Have you consulted with the network admin at your place of work?

---

### Post by dillonregi on 2018-10-16
Is it not possible to control which APs my laptop connects to?

---

### Post by him610 on 2018-10-17
Assuming you can identify the APs you do not wish to connect to, you can filter out those APs. Open up Network Connections, highlight the Undesired Name_of_AP then click to Edit,  another window  should appear, Editing Undesired_Name_of_AP. In the General tab, de-select the top line that reads, "Automatically connect to this network when available". Click the Save button, and exit from the Network Connections. You will probably need to repeat this for each of the undesired APs. Take a walk through your work facility to see if your laptop ignores those undesired APs. 
I have never experienced your particular issue, and I am not 100% sure this will work for you, but it is worth a try.

---

### Post by oldos2er on 2019-10-25
Reopened.

---

### Post by him610 on 2019-10-25
Looks like we are revisiting this issue after a year, I would think this could be addressed by editing the network manager configuration yaml file. I think you can find what you need to know by perusing *man netplan*

---

### Post by wildmanne39 on 2019-11-04
Old thread closed.

---

