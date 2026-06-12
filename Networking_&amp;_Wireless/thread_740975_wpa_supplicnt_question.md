---
title: "wpa_supplicnt question"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by grumpylad77 on 2008-03-31
Trying to connect to my schools wireless, when I launch WPA_SUPPLICANT I get this

mat@laptop:~$ Trying to associant with 00:13:1a:2a:a3:d0
Associated with 00:13:1a:2a:a3:d0
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
OpenSSL: tls_connection_handshake-Failed to read possible Application Data Error:00000000:lib(0):func(0):reason(0)
EAP-MSCHAPV2: Authentication succeeded
EAP-TLV:TLV Result-success-EAP-TLV/Phase2 Completed
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
CTRL-EVENT-CONNECTED-Connection to 00:13:1a:2a:a3:d0 completed (reath) [id=0 id_str=]


so what does this mean?
OpenSSL: tls_connection_handshake-Failed to read possible Application Data Error:00000000:lib(0):func(0):reason(0)

and is that why I cannot connect because everything else look good

---

### Post by mrm48 on 2008-04-02
I'm getting the same print out from wpa_supplicant trying to connect to a PEAP network.

I've tried a few configurations for wpa_supplicant.conf with no luck.

I'm executing wpa_supplicant with the following command:

sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -Dwext

---

### Post by kevdog on 2008-04-02
Both of you guys need to post your wpa_supplicant.conf file to display the parameters you are passing.

---

### Post by mrm48 on 2008-04-02
eapol_version=1
ap_scan=2
fast_reauth=1
network={
        ssid="tsunami"
        key_mgmt=IEEE8021X
	scan_ssid=1
        eap=PEAP
        identity="mrm48"
        password="password"
	phase1="peaplabel=0"        
	phase2="auth=MSCHAPV2"
}

---

### Post by kevdog on 2008-04-02
Where did you find the instructions how to set your configurations for PEAP?

---

### Post by mrm48 on 2008-04-02
I found it at my University's website [here]("http://support.uakron.edu/wiki/index.php/Linux_Wireless").

---

### Post by kevdog on 2008-04-02
Kind of a strange configuration however I'm trusting your admins know what they are talking about.  Are you sure your wireless interface is eth1 rather than ath0 or wlan0 or ra0 or something else? 

ifconfig should give you this needed info.

---

### Post by mrm48 on 2008-04-02
Yeah, ifconfig yields:

eth1      Link encap:Ethernet  HWaddr 00:14:A5:23:0C:86  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe23:c86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:26 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116840 (114.1 KB)  TX bytes:14483235 (13.8 MB)
          Interrupt:10 Base address:0x4000 

iwconfig shows that eth1 is connected to my network with WPA security.

---

### Post by kevdog on 2008-04-02
Try adding the -w switch, and also add a -dd switch at the end.  -dd will give you debugging output that might help.

---

