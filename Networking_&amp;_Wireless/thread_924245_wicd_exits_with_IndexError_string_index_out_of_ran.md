---
title: "wicd exits with IndexError: string index out of range when using own template"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by T-MAN3000 on 2008-09-19
I'm trying to connect to my university wireless network, which requires me to load to a certificate to wpa_supplicant. I'm using wicd (network-manager doesn't work on my Asus EEE 1000h), so I need to put together my own template. It looks like this:

```
name = UNICERT
author = me
version = 1
require identity *Username password *Password ca_cert *Path_to_CA-Cert 
-------
network={
        ssid="$_ESSID"
        scan_ssid=$_SCAN
        key_mgmt=IEEE8021X
        eap=TTLS
        phase2="auth=PAP"
        identity="$_IDENTITY"
        password="$_PASSWORD"
        ca_cert="$_CA_CERT"
}
```

now, when I start the wicd gui (/opt/wicd/gui.py) I get this error;

```
attempting to connect daemon...
success
starting gui.py...
refreshing...
Number of wireless networks detected: 1
using global dns: 0
ESSID: uva
making a new network entry...
disabling ip
disabling dns
global dns checkbox toggled False
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 1319, in <module>
    app = appGui()
  File "/opt/wicd/gui/py", line 910, in __init__
    self.refresh_networks(fresh=False)
  File "/opt/wicd/gui.py", line 1211, in refresh_networks
    tempNetwork = PrettyWirelessNetworkEntry(x)
  File "/opt/wicd/gui.py", line 321, in __init__
     PrettyNetworkEntry.__init__(self,WirelessNetworkEntry(networkID))
  File "/opt/wicd/gui.py:, line 728, in __init__
     encryptionTypes = misc.LoadEncryptionMethods()
  File "/opt/wicd/misc.py", line 124, in LoadEncryptionMethods
     if current[0] == "*":
IndexError: string index out of range
```

Of course I double-checked everything with the examples on [http://wicd.sourceforge.net/templates.php](http://wicd.sourceforge.net/templates.php) but I don't see the mistake I'm probably making. Anyone any idea?

---

### Post by imdano on 2008-09-21
Try changing ```
*Path_to_CA-Cert
``` to ```
*Path_to_CA_Cert
```You also might want to upgrade to 1.5.2, I think I rewrote some of the parsing code to handle errors a little bit better.

---

### Post by T-MAN3000 on 2008-09-22
Thanks for replying, I upgraded wicd to 1.5.2 and edited the template to look like this: (I also made some other, mostly cosmetic, changes)

```
name = EDUROAM
author = Tiemen Ruiten
version = 1
require identity *Username password *Password certificate *Path_to_CA_Cert 
-----
network={
        ssid="$_ESSID"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=TTLS
        anonymous_identity="anonymous@uva.nl"
        phase2="auth=PAP"
        identity="$_IDENTITY"
        password="$_PASSWORD"
        ca_cert="$_CERTIFICATE"
}

```

at home wicd is working flawlessly with the WPA template with a WPA2 key. This morning on my university the line constantly showing up in my wicd.log was

```
WPA_CLI RESULT IS None
```

Any idea? Thanks in advance for taking the time to respond!




edit: I did some more testing and when I run ```
wpa_supplicant -B -i ra0 -c "/var/lib/wicd/configurations/0019e81fec30" -D wext
``` 
in a shell, (I took this line from the log file) it returns:
```
Failed to read or parse configuration '/var/lib/wicd/configurations/0019e81fec30'. 
```

I'll post the whole logfile tonight.

---

