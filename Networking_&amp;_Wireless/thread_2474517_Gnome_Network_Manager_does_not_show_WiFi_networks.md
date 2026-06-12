---
title: "Gnome Network Manager does not show WiFi networks"
date: 2022-05-01
forum: Networking &amp; Wireless
---

### Post by sharbich on 2022-05-01
Hello,
I no longer see any WiFi networks in the Gnome Network Manager. I don't want to install new Ubuntu. What can I do?
I uninstalled and reinstalled the "network-manager" package with "atp-get --purge remove network-manager". Unfortunately without success.
Who can help me please?
```
(base) stefan.harbich@nmanme01:~$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:    20.04
Codename:    focal

```
Greetings from Stefan Harbich

---

### Post by sharbich on 2022-05-04
I don't see any WiFi networks in the Gnome Network Manager. What can I do?

---

### Post by jeremy31 on 2022-05-04
See the wireless script link in my signature and post results

---

### Post by sharbich on 2022-05-04
> **jeremy31 said:**
> See the wireless script link in my signature and post results
Hi,
here my Attachet.

---

### Post by jeremy31 on 2022-05-04
You changed the settings to use netplan to manage the wifi.  On my system the /etc/netplan/1-network-manager-all.yaml file contains
```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

---

### Post by sharbich on 2022-05-04
Hello,
I changed the file as follows.

```
(base) stefan.harbich@nmanme01:~$ cat /etc/netplan/01-network-manager-all.yaml.orig
# Let networkd manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
##   renderer: networkd
##   ethernets:
##     enp1s0:
##       dhcp4: true
##   wifis:
##     wlp2s0:
##       access-points:
##         "Access-Point-Harbich":
##           password: "#############"
##       dhcp4: true

```

After restarting, I still don't see any networks in the Gnome Network Manager.

---

### Post by sharbich on 2022-05-05
Hello,
the status to the network manager:
```
(base) stefan.harbich@nmanme01:~$ sudo systemctl status network-manager[sudo] Passwort für stefan.harbich: 
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2022-05-05 09:08:29 CEST; 7min ago
       Docs: man:NetworkManager(8)
   Main PID: 990 (NetworkManager)
      Tasks: 3 (limit: 9278)
     Memory: 12.6M
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;990 /usr/sbin/NetworkManager --no-daemon


Mai 05 09:13:50 nmanme01 NetworkManager[990]: <error> [1651734830.1758] sup-iface[0x5589cffc5920,wlp2s0]: error adding interface: wpa_supplicant cou>
Mai 05 09:13:50 nmanme01 NetworkManager[990]: <info>  [1651734830.1759] device (wlp2s0): supplicant interface state: starting -> down
Mai 05 09:14:00 nmanme01 NetworkManager[990]: <warn>  [1651734840.0421] device (wlp2s0): re-acquiring supplicant interface (#4).
Mai 05 09:14:00 nmanme01 NetworkManager[990]: <error> [1651734840.1831] sup-iface[0x5589cffc5920,wlp2s0]: error adding interface: wpa_supplicant cou>
Mai 05 09:14:00 nmanme01 NetworkManager[990]: <info>  [1651734840.1832] device (wlp2s0): supplicant interface state: starting -> down
Mai 05 09:14:06 nmanme01 NetworkManager[990]: <info>  [1651734846.4264] agent-manager: agent[1c9b0e015157dd58,:1.290/org.gnome.Shell.NetworkAgent/10>

```Something is not right.

---

### Post by sharbich on 2022-05-05
Hello,
i was able to solve the problem. I have deleted the following content in the "/etc/netplan/01-networkd-all.yaml" file. After the restart, the NetworkManager worked again as usual.
```
(base) stefan.harbich@nmanme01:~$ sudo cat /etc/netplan/01-networkd-all.yaml
...
-  wifis:
-    wlp2s0:
-      access-points:
-        "Access-Point-Harbich":
-          password: "#############"
-      dhcp4: true

```
Greetings from Stefan Harbich

---

