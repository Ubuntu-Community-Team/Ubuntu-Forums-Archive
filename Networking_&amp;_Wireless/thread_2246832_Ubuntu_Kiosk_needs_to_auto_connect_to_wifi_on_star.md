---
title: "Ubuntu Kiosk needs to auto connect to wifi on startup. Super frustrated :/"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by vinniepearl on 2014-10-03
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS)

So.. I followed this document and successfully created the kiosk in Ubuntu 14.04. Everything works great when I'm plugged into Ethernet; but the problem is I have 64 machines that are going to be deployed and they need to connect to wifi in kiosk mode and they aren't. 

I've been reading for about 4 hours and I'm not getting anywhere. 

The machines connect to our wifi connection and are allowed network access via Mac filtering. After the machine is added and are connecting it asks for username and password to be authenticated on the domain.

So I need to automatically connect to this wifi on boot and I'm failing horribly.

This is about as far as I got.... 

sudo gedit /etc/network/interfaces

auto lo 
iface lo inet loopback 
auto wlan0 
iface wlan0 inet dhcp

I'll attach some images below. I've spent quite a bit of time on this project and didn't anticipate this happening. Help would be very very appreciated.

---

### Post by matt_symes on 2014-10-03
Hi

I'm not sure if i can help you but maybe we can get the ball rolling for others.
```

sudo gedit /etc/network/interfaces

auto lo 
iface lo inet loopback 
auto wlan0 
iface wlan0 inet dhcp
```

Are you sure you need an entry for wlan0 in the interfaces file if you want network manager to manage that interface ?

Have you looked in network managers system-connections directory for your access point ?

```
sudo cat /etc/NetworkManager/system-connections/<access_point_name>
```

What information does it contain ? Does it contain the username/domain and password information ?

Kind regards

---

### Post by vinniepearl on 2014-10-03
First Let me supply more information that I've retrieved. The connection is wpa2 eap 802.1x authentication. 

[IMG]http://i547.photobucket.com/albums/hh448/vinniepearl/wifisecurity.jpg[/IMG]



Also, I check the file you referenced and it was empty.

sudo gedit /etc/NetworkManager/system-connections/accespointname 


I've found some information but I need some help breaking it down.

[http://www.lsi.upc.edu/lclsi/Manuales/wireless/files/wpa_supplicant.conf](http://www.lsi.upc.edu/lclsi/Manuales/wireless/files/wpa_supplicant.conf)

# EAP-PEAP/MSCHAPv2 configuration for RADIUS servers that use the new peaplabel
# (e.g., Radiator)
#network={
#	ssid="example"
#	key_mgmt=WPA-EAP
#	eap=PEAP
#	identity="user@example.com"
#	password="foobar"
#	ca_cert="/etc/cert/ca.pem"
#	phase1="peaplabel=1"
#	phase2="auth=MSCHAPV2"
#	priority=10
#}


I'll admit I'm extremely overwhelmed at the moment. Any help I really do appreciate.

---

### Post by praseodym on 2014-10-03
Change "false" to "true" in the file /etc/NetworkManager/NetworkManager.conf and reboot. Otherwise the NM cannot handle the manual entries in the "interfaces"

---

### Post by weatherman2 on 2014-10-03
If it were me, I'd invest in a cheap wireless ethernet bridge.  (I one at home to connect my media center PC to my wireless router.)   Kiosks can power off but bridge always connected; as soon as kiosks power on, they get a wired connection (to the wireless bridge).

Yes, pure WiFi should work for automatic connection but as you are finding out, it may not.

---

### Post by vinniepearl on 2014-10-03
> **weatherman2 said:**
> If it were me, I'd invest in a cheap wireless ethernet bridge.  (I one at home to connect my media center PC to my wireless router.)   Kiosks can power off but bridge always connected; as soon as kiosks power on, they get a wired connection (to the wireless bridge).

Yes, pure WiFi should work for automatic connection but as you are finding out, it may not.

These Kiosk's are going in a very large warehouse and will be very spread out; also the budget limit has been reached so no more spending. I've spent a week setting the kiosk's up and the absolute last thing I need to do before imaging 64 of them is get them to connect to the wifi automatically as they boot directly to kiosk mode.

---

### Post by matt_symes on 2014-10-03
Hi

> 
I've found some information but I need some help breaking it down.

[http://www.lsi.upc.edu/lclsi/Manuale...upplicant.conf]("http://www.lsi.upc.edu/lclsi/Manuales/wireless/files/wpa_supplicant.conf")

# EAP-PEAP/MSCHAPv2 configuration for RADIUS servers that use the new peaplabel
# (e.g., Radiator)
#network={
#    ssid="example"
#    key_mgmt=WPA-EAP
#    eap=PEAP
#    identity="user@example.com"
#    password="foobar"
#    ca_cert="/etc/cert/ca.pem"
#    phase1="peaplabel=1"
#    phase2="auth=MSCHAPV2"
#    priority=10
#}

That's not the correct format that network manager stores it access point information in. 

That's the format you use to create a wpa_supplicant.conf file that you pass to the wpa_supplicant binary when you want to connect via the command line or when executing the wpa_supplicant binary.

Network Manager stores its information in a different format (an .ini file format) the format above.

Here's a real example from the open wireless network at my local library.
```

matthew-laptop:/home/matthew % sudo cat /etc/NetworkManager/system-connections/Libraries
[connection]
id=Libraries
uuid=029e67b7-03c7-4d1d-81c9-a4c3f1987e83
type=802-11-wireless

[802-11-wireless]
ssid=Libraries
mode=infrastructure
mac-address=C0:54:3D:D7:73:C9

[ipv6]
method=auto

[ipv4]
method=auto
matthew-laptop:/home/matthew % 
```

Anyway, i created a test connection to a WPA-PEAP access point with almost the same settings as yours.

```

[connection]
id=WPA-PEAP
uuid=796b0f26-e632-4f05-ae79-0fb81ecfce6f
type=802-11-wireless

[802-11-wireless]
ssid=test_wpa_peap
mode=infrastructure
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-eap

[ipv4]
method=auto

[ipv6]
method=auto

[802-1x]
eap=peap;
identity=domain/user
phase2-auth=mschapv2
password-flags=1
matthew-laptop:/etc/NetworkManager/system-connections:0 % 
```

Does yours look similar ?

I don't really have any answers as to why it's not remembering your passwords. I'm just hoping that we'll be able to starting asking the right questions....

.... like maybe 'what does password-flags=1 mean' ?

Kind regards

---

