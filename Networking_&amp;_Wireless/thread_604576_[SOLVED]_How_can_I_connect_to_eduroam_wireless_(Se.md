---
title: "[SOLVED] How can I connect to eduroam wireless (SecureW2) in Ubuntu 7.10?"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Wienerschnitzel on 2007-11-06
Look guys, bear with me. I'm pretty much a beginner where Linux is considered, so I decided to include as much text as I thought was relevant. 

I've been working on this for a while and haven't been able to connect to eduroam yet. This annoys me. I jumped to Linux because of stability issues and general Windows irritation, but I want my internet!

Naturally I looked around the net first. There seem to be quite a few people with this 'problem', but no simple catch-all solution. I went with a suggestion on my educational institution's IT forum, but it didn't work. It does look promising, however.

A friend of mine looked at the error log and said I was getting close, but I still can't figure out what I'm doing wrong or why, for that matter.

The guide on the forum starts by recommending users to make a .pem certificate file which I named HvAcertificate.pem:

```

-----BEGIN CERTIFICATE-----
MIICkDCCAfmgAwIBAgIBATANBgkqhkiG9w0BAQQFADBaMQswCQYDVQQGEwJVUzEc
MBoGA1UEChMTRXF1aWZheCBTZWN1cmUgSW5jLjEtMCsGA1UEAxMkRXF1aWZheCBT
ZWN1cmUgR2xvYmFsIGVCdXNpbmVzcyBDQS0xMB4XDTk5MDYyMTA0MDAwMFoXDTIw
MDYyMTA0MDAwMFowWjELMAkGA1UEBhMCVVMxHDAaBgNVBAoTE0VxdWlmYXggU2Vj
dXJlIEluYy4xLTArBgNVBAMTJEVxdWlmYXggU2VjdXJlIEdsb2JhbCBlQnVzaW5l
c3MgQ0EtMTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAuucXkAJlsTRVPEnC
UdXfp9E3j9HngXNBUmCbnaEXJnitx7HoJpQytd4zjTov2/KaelpzmKNc6fuKcxtc
58O/gGzNqfTWK8D3+ZmqY6KxRwIP1ORROhI8bIpaVIRw28HFkM9yRcuoWcDNM50/
o5brhTMhHD4ePmBudpxnhcXIw2ECAwEAAaNmMGQwEQYJYIZIAYb4QgEBBAQDAgAH
MA8GA1UdEwEB/wQFMAMBAf8wHwYDVR0jBBgwFoAUvqigdHJQa0S3ySPY+6j/s1dr
aGwwHQYDVR0OBBYEFL6ooHRyUGtEt8kj2Puo/7NXa2hsMA0GCSqGSIb3DQEBBAUA
A4GBADDiAVGqx+pf2rnQZQ8w1j7aDRRJbpGTJxQx78T3LUX47Me/okENI7SS+RkA
Z70Br83gcfxaz2TE4JaY0KNA4gGK7ycH8WUBikQtBmV1UsCGECAhX2xrD2yuCRyv
8qIYNMR1pHMc8Y3c7635s3a0kr/clRAevsvIO1qEYBlWlKlV
-----END CERTIFICATE-----
```

With a little research I managed to find out that my university is using the Equifax Secure Global eBusiness certificate, but the .pem I made and the .crt in my /usr/share/ca-certificates/mozilla/ dir seem to employ different breaks. I don't know whether this is relevant.

Equifax_Secure_Global_eBusiness_CA.crt:

```

-----BEGIN CERTIFICATE-----
MIICkDCCAfmgAwIBAgIBATANBgkqhkiG9w0BAQQFADBaMQswCQYDVQQGEwJV
UzEcMBoGA1UEChMTRXF1aWZheCBTZWN1cmUgSW5jLjEtMCsGA1UEAxMkRXF1
aWZheCBTZWN1cmUgR2xvYmFsIGVCdXNpbmVzcyBDQS0xMB4XDTk5MDYyMTA0
MDAwMFoXDTIwMDYyMTA0MDAwMFowWjELMAkGA1UEBhMCVVMxHDAaBgNVBAoT
E0VxdWlmYXggU2VjdXJlIEluYy4xLTArBgNVBAMTJEVxdWlmYXggU2VjdXJl
IEdsb2JhbCBlQnVzaW5lc3MgQ0EtMTCBnzANBgkqhkiG9w0BAQEFAAOBjQAw
gYkCgYEAuucXkAJlsTRVPEnCUdXfp9E3j9HngXNBUmCbnaEXJnitx7HoJpQy
td4zjTov2/KaelpzmKNc6fuKcxtc58O/gGzNqfTWK8D3+ZmqY6KxRwIP1ORR
OhI8bIpaVIRw28HFkM9yRcuoWcDNM50/o5brhTMhHD4ePmBudpxnhcXIw2EC
AwEAAaNmMGQwEQYJYIZIAYb4QgEBBAQDAgAHMA8GA1UdEwEB/wQFMAMBAf8w
HwYDVR0jBBgwFoAUvqigdHJQa0S3ySPY+6j/s1draGwwHQYDVR0OBBYEFL6o
oHRyUGtEt8kj2Puo/7NXa2hsMA0GCSqGSIb3DQEBBAUAA4GBADDiAVGqx+pf
2rnQZQ8w1j7aDRRJbpGTJxQx78T3LUX47Me/okENI7SS+RkAZ70Br83gcfxa
z2TE4JaY0KNA4gGK7ycH8WUBikQtBmV1UsCGECAhX2xrD2yuCRyv8qIYNMR1
pHMc8Y3c7635s3a0kr/clRAevsvIO1qEYBlWlKlV
-----END CERTIFICATE-----
```

Having made a certificate (to reiterate: I use the .pem file), I followed the next step in the guide. Basically I had to make a config file for wpa_supplicant and write a script / use the terminal to load the config file.

My wpa_supplicant.conf file:

```

ctrl_interface=/var/run/wpa_supplicant
	eapol_version=1
	ap_scan=1
	fast_reauth=1
	network={
		ssid="eduroam"
		key_mgmt=IEEE8021X
		proto=WPA
		eap=TTLS
		identity="username@hva.nl"
		password="password"
		phase2="auth=PAP"
		ca_cert="/etc/wpa_supplicant/CA/HvAcertificate.pem"
		ca_path="/etc/wpa_supplicant/CA/"
		priority=2
		}
```

Now for the script I use to load it:

```

#!/bin/bash

sudo ifconfig eth1 down
sudo killall NetworkManager
sudo wpa_supplicant -i eth1 -D wext -c /etc/wpa_supplicant.conf
sudo dhclient eth1
```

Note that this script was written by my friend for my first attempt at connecting to the eduroam network. I didn't alter it after I changed the wpa_supplicant.conf file according to the guide, since the shell script basically does the same as the terminal commands they recommend.

So now I'm all set. I fire up SecureW2.sh (har har) to load wpa_supplicant.conf and... a whole lot of nothing. No actual connection, although the authentication is going through (as far as I can tell from the readout in the terminal). 

So what do I do? I make an error log and post it on the Ubuntu fora, of course!

My error log:

```

NetworkManager: no process killed
Trying to associate with 00:0d:ed:77:d9:0d (SSID='eduroam' freq=2412 MHz)
Associated with 00:0d:ed:77:d9:0d
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
CTRL-EVENT-CONNECTED - Connection to 00:0d:ed:77:d9:0d completed (auth) [id=0 id_str=]

CTRL-EVENT-TERMINATING - signal 2 received
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:dc:e9:59
Sending on   LPF/eth1/00:13:02:dc:e9:59
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.0.150
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
```

And here we are! Typically, line 4 through 8 in the event log/error log will repeat themselves for a while, until I hit ctrl+c. I'm stumped.

I hope somebody can tell me what I'm doing wrong and what I need to do in order to remedy the problem.

---

### Post by PaulFr on 2007-11-06
I am not familiar with eduroam, but I would suggest you change the wpa_supplicant line to read: > sudo wpa_supplicant -B -i eth1 -D wext -c /etc/wpa_supplicant.conf -ddand try.  *-B to go into daemon mode, and -dd to give you oodles of debug logging*

For more details and suggestions, please see **[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)**.

---

### Post by Wienerschnitzel on 2007-11-07
Thanks for the tip, PaulFr! I can now access eduroam under Linux. In essence, I didn't change much.

I'm still using HvAcertificate.pem as my authentication certificate, but I made a few minor changes in the wpa_supplicant.conf file and my SecureW2.sh load script. I'll post them below for future reference in case somebody else runs into this problem.

In wpa_supplicant.conf I only added the ca_path line. It was mentioned somewhere that this should be done because wpa_supplicant can run from different locations or something, and fail to find the certificate because it can't find the dir:

```

ctrl_interface=/var/run/wpa_supplicant
	eapol_version=1
	ap_scan=1
	fast_reauth=1
	network={
		ssid="eduroam"
		key_mgmt=IEEE8021X
		proto=WPA
		eap=TTLS
		identity="username@hva.nl"
		password="password"
		phase2="auth=PAP"
		ca_cert="/etc/wpa_supplicant/CA/HvAcertificate.pem"
		ca_path="/etc/wpa_supplicant/CA/"
		priority=2
		}
```

In securew2.sh I merely added your suggestions, which yields the following results:

```

#!/bin/bash

sudo ifconfig eth1 down
sudo killall NetworkManager
sudo wpa_supplicant -B -i eth1 -D wext -c /etc/wpa_supplicant.conf -dd
sudo dhclient eth1

```

In my case, this solved all the problems. I disconnected a few times and managed to reconnect again to be sure it wasn't a chance encounter with a compliant router. I also rebooted and connected, which also worked. The final test was moving around the building, out of range of the original router I connected to. This demonstrated that roaming also works with this .conf file.

If you're reading this because you ran into the same problems as I did, it's very unlikely that you're also a student at the Hogeschool van Amsterdam (HvA). This means that your institution probably uses a different certificate to authenticate the connection. Ask your IT helpdesk which one they use, and you should be able to find it in the CA_certificates package accessible through the Synaptic Package Manager.

In any case, good luck!

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

