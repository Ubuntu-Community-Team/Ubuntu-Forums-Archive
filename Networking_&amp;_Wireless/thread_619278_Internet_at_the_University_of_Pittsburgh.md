---
title: "Internet at the University of Pittsburgh"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by gamesetmatch on 2007-11-21
To access the network at Pitt, here is what is needed to be done:
1. Create the following file.
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=0
network={
key_mgmt=WPA-EAP
eap=PEAP
priority=10
}
Name this file wpa.conf.
2. From the a command prompt enter the following commands (the $ represents 
the command prompt).
Following each of these commands you will be prompted for your root 
password.
$ sudo ifconfig eth0 up
$ sudo wpa_supplicant -B -Dwired -ieth0 -cwpa.conf
These commands turn on your ethernet connection and the WPA Supplicant 
daemon.
3. From the command line type the following command the enter the WPA 
client:
$ sudo wpa_cli
You should now be in the WPA client.
4. In the WPA client type the following changing USERNAME to your username 
and PASSWORD to your
password. (The > represents the prompt and is not to be typed.)
> identity 0 USERNAME
> password 0 PASSWORD
> quit

Step 2 is the one I'm am trying to avoid having to do every single time.  Is their a way to have my internet connection do this automatically?  I am using Network Manager.  Any help is appreciated, no rush as well.

---

### Post by Blutack on 2007-11-21
Pop it all in a shell script and run it at boot up.  Or try something like wicd, although I don't know if that supports PEAP over wired.  The problem seems to be that wpa_supplicant will only use one driver at a time by default.  If nothing else pop it in a script and make a panel launcher with gksu 'net.sh' (just knock off the sudo's first).

---

### Post by gamesetmatch on 2007-11-28
I'm new to Ubuntu, could you explain how I would do that?

---

### Post by Whiffle on 2007-11-28
You can add all that to /etc/network/interfaces and it will do it automatically every time the interface is brought up.

something like this:
```

 auto lo
 iface lo inet loopback
 
 auto eth0
 iface eth0 inet dhcp
 wpa-driver wired
 wpa-eap PEAP
 wpa-key-mgmt WPA-EAP
 wpa-priority 10
 wpa-identity <username here>
 wpa-password <password here>

 

```

---

