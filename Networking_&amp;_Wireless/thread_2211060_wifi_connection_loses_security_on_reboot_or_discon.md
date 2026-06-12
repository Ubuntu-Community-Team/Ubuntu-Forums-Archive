---
title: "wifi connection loses security on reboot or disconnect/reconnect"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by mamboze on 2014-03-13
Hi,
I've got this problem with my wifi connection on ubuntu 12.04. After I have set the WPA security on the connection (TP-LINK_6FAD25) it persists for the current session. But on a reboot or disconnect/reconnect, a new copy is made (TP-LINK_6FAD25 1, TP-LINK_6FAD25 2  etc) which has no security. If I set the security for this copy, it persists as before. Also, I've tried to change the name of the connection to something more familiar but I can't get this to come up on the wifi drop down list. 

i'm rather bored with having to do these repetitive resets, so any help would be much appreciated  :)

---

### Post by varunendra on 2014-03-14
Are you also manually saving any MAC address in BSSID or "Device MAC address" field?

Can we see the key files for both connections? They are located in "/etc/NetworkManager/system-connections" directory, and need root privileges to read them. Assuming their names are as you mentioned above, you can use the following commands to read them -
```
[s]sudo cat "/etc/NetworkManager/system-connections/TP-LINK_6FAD25 1"[/s] #Better use the command below to omit the "psk" part for security
[s]sudo cat "/etc/NetworkManager/system-connections/TP-LINK_6FAD25 2"[/s] #Better use the command below to omit the "psk" part for security

sudo egrep -v '(psk|password|identity)=' /etc/NetworkManager/system-connections/*<Connection Name here>*
```

**[COLOR="#FF0000"]CAUTION![/COLOR]** It may also have your saved **[COLOR="#FF0000"]security key[/COLOR]**. _Delete or Obscure it before posting_ the above output here.

**EDIT:** Edited the command for better security, in case the user forgets to remove the security key while posting, like the OP did..

---

### Post by mamboze on 2014-03-14
OK,
output for    sudo cat "/etc/NetworkManager/system-connections/TP-LINK_6FAD25 1"
```
[connection]
id=TP-LINK_6FAD25 1
uuid=93017a5e-6ab2-45c9-9556-5a10787fb7d1
type=802-11-wireless
timestamp=1394849387

[802-11-wireless]
ssid=TP-LINK_6FAD25
mode=infrastructure
mac-address=4C:ED:DE:F5:6F:56
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=<snip>

[ipv4]
method=auto

[ipv6]
method=auto


```
and    sudo cat "/etc/NetworkManager/system-connections/TP-LINK_6FAD25 2"
```

[connection]
id=TP-LINK_6FAD25 2
uuid=04347b61-f22a-44c9-8bbe-9dc793547875
type=802-11-wireless
timestamp=1394849675

[802-11-wireless]
ssid=TP-LINK_6FAD25
mode=infrastructure
mac-address=4C:ED:DE:F5:6F:56
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=<snip>

[ipv4]
method=auto

[ipv6]
method=auto
```

I checked out the model and MAC details of the modem and found that they were:
TD-W8961ND  
64:66:B3:6F:AD:25

I put this MAC into a new wifi object but on rebooting the connection the previous MAC  4C:ED: DE:F5:6F:56 (eth1) was in the configuration (and the previous security setting was absent).

Please any suggestions? :)

---

### Post by varunendra on 2014-03-15
> **mamboze said:**
> I put this MAC into a new wifi object but on rebooting the connection the previous MAC  4C:ED: DE:F5:6F:56 (eth1) was in the configuration (and the previous security setting was absent).

This is your problem. Don't put any MAC address anywhere, let it pick it up automatically. It may even stay blank, that's not a problem.

That field (Device MAC address) needs to be manually configured ONLY if you have more than one Network card of the same kind (wireless in this case) and you want to use any specific one, OR if you want to "FIX" the connection to a specific Access-Point (the BSSID field).

Just Leave that tab entirely the way it is, save your security settings under the security tab, change the "Connection name" if you wish to > Save > close.

Reboot and I hope it will stay this time.

---

### Post by mamboze on 2014-03-15
Hi,

I created a new connection with no MAC information, as you suggested. Saved it. Rebooted the laptop and modem. 

After the reboot, there was no wifi connection, I checked the TPL-LINK_6FFAD25 entry in the dropdown, it had no MAC and WPA security, as configured prior to the reboot.   So I selected TPL-LINK_6FFAD25, this generated, as before, a new connection, TPL-LINK_6FFAD25 1  which had no security settings and had the MAC address. Another thing I've noticed is that the connection I set up with a new connection name shows up in the list of available and editable connections but not in the selection drop down. 

Thank you for editing my p/w out. I saw it there but forgot to do the edit myself. Please pardon my ignorance about modems etc.

---

### Post by varunendra on 2014-03-15
> **mamboze said:**
> So I selected TPL-LINK_6FFAD25, this generated, as before, a new connection, TPL-LINK_6FFAD25 1  which had no security settings and had the MAC address.
This is the only thing you need to do ^^. The number "1" was added because you already added a connection previously, with no security key.

Don't create any connections beforehand (you can, but don't), delete the existing ones pertaining to this connection. Reboot, and click the name from "Available" connections. It should ask you the security key, provide it.

At this point, a new (and only, since you deleted the previous connections) connection would be created and the security key (that you provided to get connected) should be automatically saved in it.

Since next boot, it should get connected automatically as soon as the network is found. If anything is not happening (security key not automatically saved, not connecting automatically etc.), let me know, and we'll check what is remaining. But don't do anything manually (again, you can, but for now - don't). Only choose network > provide your password > let the system do the rest.

---

### Post by mamboze on 2014-03-15
OK, I deleted all connections related to my internet provider (leaving two for other locations). On reboot, after selecting from Available list, it connected without asking for a security p/w. I did an edit on that connection and it had no security settings. So I set up WPA Personal on it. 

Rebooting again, the connection was not made automatically. So I had to select from Available which of course generated the second connection as it has done before.....

---

### Post by varunendra on 2014-03-15
> **mamboze said:**
> On reboot, after selecting from Available list, **[COLOR="#FF0000"]it connected without asking for a security p/w[/COLOR]**.

I'm not getting this part. If your access-point has a security password, how come you could connect WITHOUT providing that on a fresh attempt?

Please post back the outputs of (while being connected to the network in question) -
```
sudo iwlist scan
ls -la /etc/NetworkManager/system-connections/*
```

In the first command's output, I want to confirm if your access-point actually requires a security key at all.

In the second command's output, I want you to confirm if you see any unidentified or previously existing connections (pertaining to this network).

---

### Post by mamboze on 2014-03-15
Hi,

Here are the requested outputs

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 64:66:B3:6F:AD:25
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:off
                    ESSID:"TP-LINK_6FAD25"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000E54502D4C494E4B5F364641443235
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608070000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555300010B10
          Cell 02 - Address: C0:4A:00:FF:9A:55
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"NATCHA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00064E4154434841
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555300010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010014
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: 64:66:B3:6F:AB:96
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"AIR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0003414952
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555300010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010030
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000

```

NATCHA and AIR are, as you would of course know, two wifi modems in my immediate vicinity. 

```
ls -la /etc/NetworkManager/system-connections/*
-rw------- 1 root root 299 Mar 14 15:27 /etc/NetworkManager/system-connections/SITI
-rw------- 1 root root 310 Mar 15 21:36 /etc/NetworkManager/system-connections/TP-LINK_6FAD25
-rw------- 1 root root 341 Mar 16 05:37 /etc/NetworkManager/system-connections/TP-LINK_6FAD25 1
-rw------- 1 root root 321 Mar 12 20:44 /etc/NetworkManager/system-connections/y54213963

```

Regarding this output, SITI and y54213963 are 2 sites I access with wifi regularly. The other 2 you know about ... 

Thank you for your continuing help, I appreciate it very much.

Roy

---

### Post by mamboze on 2014-03-15
Hi,

The cell01 section of the iwlist scan output has the setting: Encryption key: off. I thought that if this were set on, it would force a request for a key on startup.
But it is not consistent with the settings in the file /etc/NetworkManager/system-connections/TP-LINK_6FAD25

```

[connection]
id=TP-LINK_6FAD25
uuid=932a2bee-eb32-46e7-ab9f-c57fc4727598
type=802-11-wireless
timestamp=1394893927

[802-11-wireless]
ssid=TP-LINK_6FAD25
mode=infrastructure
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=<snip>

[ipv4]
method=auto

[ipv6]
method=auto

```

There is also the question of why the connection is not made automatically, despite automatic connection being checked in edit connections  ???

---

### Post by varunendra on 2014-03-16
So as you realized, your access-point has no security enabled (which is not good). Hence why the connection is recreated when you manually add a security key to it. It simply no more remains the 'Same' connection (the one you 'Saved' *should be* a secured one, while the one you are actually connecting to is not).

> **mamboze said:**
> The cell01 section of the iwlist scan output has the setting: Encryption key: off. I thought that if this were set on, it would force a request for a key on startup.
Exactly. You should immediately enable an appropriate security on the access-point (I recommend WPA2-AES (CCMP), keep away from WPA/WPA2 mixed mode and TKIP).

The inconsistency you see in the file was probably imposed by yourself? If you don't try to save a security password, the file shouldn't contain that part. Of course saving the password will be required (and should happen automatically, as mentioned previously) once you enable security in the router.

About this -
> There is also the question of why the connection is not made automatically, despite automatic connection being checked in edit connections  ???
I would assume it is happening due to the confusion of having multiple files with same settings except the security key.

---

