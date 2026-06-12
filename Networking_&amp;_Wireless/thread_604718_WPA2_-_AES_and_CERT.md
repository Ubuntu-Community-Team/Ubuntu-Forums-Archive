---
title: "WPA2 - AES and CERT"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by luccom on 2007-11-06
I am trying to connect to wap2 enterprise network using a user certificate. With MS I am in configuring the connection as WAP2 - AES with Smart card or user certificate and it is working fine. How can I connect with Ubuntu ?

---

### Post by luccom on 2007-11-22
Is there someone with any experience with wap2 and certificate ?

---

### Post by luccom on 2007-12-17
I almost got it working !

This is my wap_supplicant.conf

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=1

network={
	ssid="dtm-guest"
	key_mgmt=NONE
	priority=10
	disabled=1
}

network={
	ssid="FenusCam"
	psk=*******
	priority=5
	disabled=1
	id_str="FenusCam"
}

network={
	ssid="LEBBiz"
	proto=RSN
	key_mgmt=WPA-EAP
	pairwise=CCMP
	eap=TLS
	identity="luccom@fen.com"
	password="******"
	ca_cert="/home/luccom/vmware/Share/Cert/luccom.pem"
}

```
The problem I am having now is that my Microsoft IAS server will not authenticate my Ubuntu.

I am getting the error message in the event viewer:
```
...
Authentication-Type = EAP
EAP-Type = <undetermined>
Reason-Code = 22
Reason = The client could not be authenticated because the Extensible Authentication Protocol (EAP) Type cannot be processed by the server.
...
```

When I successfully connect with a MS client this is what I get:

```
...
Authentication-Type=EAP
EAP-Type = Smart Card or other certificate
...
```

I tried using:
eap=MD5
eap=TLS
eap=MSCHAPV2
eap=PEAP
eap=TTLS
eap=GTC
eap=OTP
eap=LEAP
eap=PSK
eap=PAX

But it will not authenticate with the IAS server.

---

### Post by kevdog on 2007-12-17
Wish I knew anthing on the topic.  Please post a solution when you get one so we can add it to the documentation.

---

### Post by TheBronze on 2007-12-20
I am trying to do a similar thing here at work. We have a Cisco wireless using WPA2 and AES authentication with a .cer certificate.

I'm fairly new to the linux/ubuntu scene and don't have much experience with this. So any progress you make is appreciated!

---

### Post by luccom on 2007-12-20
I see that I am not the only one trying this !

Here is my /ect/network/interfaces file
```
auto lo
iface lo inet loopback

allow-hotplug eth1
iface eth1 inet manual
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant.conf

iface default inet dhcp

iface FenusCam inet static
        address 10.32.50.100
        netmask 255.255.0.0
        network 10.32.0.0
        broadcast 10.32.255.255
        gateway 10.32.50.1
        dns-nameservers 172.30.1.10
```

For my certificate I did a export (pfx file)  from a MS XP.
on the Ubuntu I did this command:

```
openssl pkcs12 -in luccom.pfx -out luccom.pem -nodes -clcerts
```

To bring the interface up  I use the command :

```
sudo ifup eth1
```

Then I use wpa_gui to check the connection:

[PHP]sudo wpa_gui[/PHP]

I hope it can help someone !

---

### Post by TheBronze on 2007-12-20
Hmm. can't get my Xp workstaion to export as a PFX. The option is greyed out. :( Tried using your command with the.cer file and it choked.

---

### Post by luccom on 2007-12-20
to export the cert I used IE
tools - internet options - content- certificates
select your certificate and export (if the certificate is no selected it will not work)

In the wizard I:
Export the private key
pfx with strong protection

This is what I did.

---

### Post by TheBronze on 2007-12-20
Ya, thats where I went, but for some reason the pfx option is greyed out.

---

### Post by pedor on 2007-12-26
> **TheBronze said:**
> Ya, thats where I went, but for some reason the pfx option is greyed out.

Same problem here :-?
I will use ubuntu in my school.

---

### Post by pedor on 2008-01-28
Bump!
I have tried Cain & Abel on XP but can´t find anything info about my wireless networks.:sad:

---

