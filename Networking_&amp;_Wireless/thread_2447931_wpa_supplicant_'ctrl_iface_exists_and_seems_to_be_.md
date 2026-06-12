---
title: "wpa_supplicant: 'ctrl_iface exists and seems to be in use - cannot override it'"
date: 2020-07-29
forum: Networking &amp; Wireless
---

### Post by durexlw on 2020-07-29
_Ubuntu server 20.04 LTS_
[SIZE=3][B]
[SIZE=2]The error message[/SIZE]
[/B][/SIZE]```
ctrl_iface exists and seems to be in use - cannot override it
Delete '/run/wpa_supplicant/wlx00c0caaa58da' manually if it is not used anymore
Failed to initialize control interface '/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was left by an unclean termination of wpa_supplicant in which case you will need to manually remove this file before starting wpa_supplicant again.
```
Somehow it seems to be I'm running two instances of wpa_supplicant?

**Some information:**
```

$ cat /etc/network/interfaces:
/etc/network/interfaces: No such file or directory
$ cat /etc/wpa_supplicant/wpa_supplicant.conf
/etc/wpa_supplicant/wpa_supplicant.conf: No such file or directory
$ cat /etc/conf.d/net
/etc/conf.d/net: No such file or directory
```
(The above is to show that I didn't define any of those files)

**My netplan config file (I have only one file in the directory '/etc/netplan'):**
```
network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    wifis:
        wlx00c0caaa58da:
            dhcp4: true
            optional: true
            access-points:
                "TelenetWiFree":
                    auth:
                        key-management: eap
                        method: peap
                        identity: xxxxxxxxxxxxxx
                        password: xxxxxxxxxxxxxx
                        phase2-auth: MSCHAPV2


```
"sudo netplan generate" just works fine without any error and "sudo netplan apply" seems to work just fine. The odd thing is: once booted, I can run netplan apply all I want, the error never shows up in my logs.

**What I did so far:**
[LIST]
[*]I removed the file manually as the error message suggests, but it persists
[*]I check this forums, but most posts are from before 2016 and most solutions are about some typo in commands like "wpa_supplicant -B -i wlan0 -c<(wpa_passphrase internet password) && dhcpcd wlan0" or about running wpa_supplicant as a daemon... all of which don't seem to apply, since I do none of that, at least: not that I know of
[/LIST]
**My main question**
[LIST]
[*]If somebody knows the answer as to why this happens, I'd be happy to know
[*]But another question I have is: in this one I don't even know where to begin debugging this? How would I go about pinpointing this problem? There seem to be mechanisms in play I don't understand yet and I'd be interested to know what they are.
[/LIST]

---

