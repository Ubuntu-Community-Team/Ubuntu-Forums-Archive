---
title: "Trouble with Intel 3165 wifi card and 20.04.4 server"
date: 2022-05-21
forum: Networking &amp; Wireless
---

### Post by mdhankins1 on 2022-05-21
I have a NUC-size box that I'm trying to get to work as a home lab server with Ubuntu Server 20.04.4. At this point I don't have a wired network, so I've been trying to get the wifi to work. Not sure why, but I can't get it to see any access points. I have confirmed that the driver and firmware are working properly.


For now I am using a wifi extender that has a ethernet port, connecting to the ethernet port on the NUC box so I can get it on the network for updates and remote management via ssh. It takes up more space than I'd like, so I don't want to use this as a long term solution.


If anyone has suggestions for how to get the onboard wifi card to work, I'd appreciate it very much.


Here's some output of what I have been looking at so far:


######################################

user1@server1:/etc/apt$ lspci|grep Wireless


01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)


user1@server1:~$ dmesg|grep iwl


[ 7.477760] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)


[ 7.480979] iwlwifi 0000:01:00.0: Found debug destination: EXTERNAL_DRAM


[ 7.480982] iwlwifi 0000:01:00.0: Found debug configuration: 0


[ 7.481330] iwlwifi 0000:01:00.0: loaded firmware version 29.1654887522.0 op_mode iwlmvm


[ 7.613668] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210


[ 7.634058] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM


[ 7.634490] iwlwifi 0000:01:00.0: Allocated 0x00400000 bytes for firmware monitor.


[ 7.639355] iwlwifi 0000:01:00.0: base HW address: c0:b6:f9:9d:32:8f


[ 7.698338] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'


[ 7.704042] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0


[ 7.777941] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM


[ 7.856332] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM


[ 7.857754] iwlwifi 0000:01:00.0: FW already configured (0) - re-configuring


user1@server1:~$ nmcli d


DEVICE TYPE STATE CONNECTION


wlp1s0 wifi unavailable --


enp2s0 ethernet unmanaged --


lo loopback unmanaged --


user1@server1:~$ nmcli radio wifi


enabled


user1@server1:~$ nmcli dev wifi list


IN-USE BSSID SSID MODE CHAN RATE SIGNAL BARS SECURITY

---

### Post by chili555 on 2022-05-21
Are there any clues here?

```
sudo dmesg | grep wlp

```
Or here?

```
sudo ip link set wlp1s0 up
sudo iwlist wlp1s0 scan
```

What does this tell us?

```
cat /etc/netplan/*.yaml
```

Is wpasupplicant installed?

```
sudo dpkg -s wpasupplicant | grep Status
```

---

### Post by mdhankins1 on 2022-05-21
When I run sudo iwlist wlp1s0 scan, it does finally see a bunch of SSIDs.

Forgot to mention that I do have a netplan file.

$ cat 00-installer-config.yaml 
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp2s0:
      optional: true 
      dhcp4: true
  version: 2
  wifis:
    wlp1s0:
      optional: true
      dhcp4: true
      access-points:
          "MyNetwork":
              password: "***********"

The actual ssid and password match what I am using for my home wifi network.  Shouldn't it just connect if the netplan has all the correct info?

$ sudo dpkg -s wpasupplicant|grep Status
Status: install ok installed

Sorry about the formatting for the yaml file above.  On my system it appears correct.  I did a quick reply and don't see how to use "code" like you did.

---

### Post by chili555 on 2022-05-21
> Shouldn't it just connect if the netplan has all the correct info?It won't connect automatically with the declaration: optional:true in the wifi section. Please remove it taking care to preserve the correct spacing, indentation, etc. Follow with:

```
sudo netplan generate
sudo netplan apply
```

Reboot and tell us if you connected.

---

### Post by mdhankins1 on 2022-05-21
I did that and afterward it did not pick up an IP from dhcp.

```

$ sudo netplan generate

$ sudo netplan apply

$ ip a s
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:e0:4c:e0:01:2f brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.172/24 metric 100 brd 192.168.0.255 scope global dynamic enp2s0
       valid_lft 7197sec preferred_lft 7197sec
    inet6 2601:204:c900:40ac:2e0:4cff:fee0:12f/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 299sec preferred_lft 299sec
    inet6 fe80::2e0:4cff:fee0:12f/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether c0:b6:f9:9d:32:8f brd ff:ff:ff:ff:ff:ff


$ sudo netplan --debug apply
** (generate:1923): DEBUG: 16:13:17.496: starting new processing pass
** (generate:1923): DEBUG: 16:13:17.496: wlp1s0: adding wifi AP 'MySSID'
** (generate:1923): DEBUG: 16:13:17.496: We have some netdefs, pass them through a final round of validation
** (generate:1923): DEBUG: 16:13:17.496: enp2s0: setting default backend to 1
** (generate:1923): DEBUG: 16:13:17.496: Configuration is valid
** (generate:1923): DEBUG: 16:13:17.496: wlp1s0: setting default backend to 1
** (generate:1923): DEBUG: 16:13:17.496: Configuration is valid
** (generate:1923): DEBUG: 16:13:17.496: Generating output files..
** (generate:1923): DEBUG: 16:13:17.496: openvswitch: definition enp2s0 is not for us (backend 1)
** (generate:1923): DEBUG: 16:13:17.496: NetworkManager: definition enp2s0 is not for us (backend 1)
** (generate:1923): DEBUG: 16:13:17.496: Creating wpa_supplicant config
** (generate:1923): DEBUG: 16:13:17.496: wlp1s0: Creating wpa_supplicant configuration file run/netplan/wpa-wlp1s0.conf
** (generate:1923): DEBUG: 16:13:17.496: Creating wpa_supplicant unit /run/systemd/system/netplan-wpa-wlp1s0.service
** (generate:1923): DEBUG: 16:13:17.498: Creating wpa_supplicant service enablement link /run/systemd/system/systemd-networkd.service.wants/netplan-wpa-wlp1s0.service
** (generate:1923): DEBUG: 16:13:17.498: openvswitch: definition wlp1s0 is not for us (backend 1)
** (generate:1923): DEBUG: 16:13:17.498: NetworkManager: definition wlp1s0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, reloading networkd
DEBUG:enp2s0 not found in {}
DEBUG:wlp1s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp2s0:
      dhcp4: true
      optional: true
  version: 2
  wifis:
    wlp1s0:
      access-points:
        MySSID:
          password: *************
      dhcp4: true


DEBUG:no netplan generated NM configuration exists
DEBUG:enp2s0 not found in {}
DEBUG:wlp1s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp2s0:
      dhcp4: true
      optional: true
  version: 2
  wifis:
    wlp1s0:
      access-points:
        MySSID:
          password: ********
      dhcp4: true


DEBUG:Link changes: {}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp2s0
DEBUG:netplan triggering .link rules for wlp1s0
** (process:1921): DEBUG: 16:13:17.853: starting new processing pass
** (process:1921): DEBUG: 16:13:17.853: wlp1s0: adding wifi AP 'MySSID'
** (process:1921): DEBUG: 16:13:17.854: We have some netdefs, pass them through a final round of validation
** (process:1921): DEBUG: 16:13:17.854: enp2s0: setting default backend to 1
** (process:1921): DEBUG: 16:13:17.854: Configuration is valid
** (process:1921): DEBUG: 16:13:17.854: wlp1s0: setting default backend to 1
** (process:1921): DEBUG: 16:13:17.854: Configuration is valid
DEBUG:enp2s0 not found in {}
DEBUG:wlp1s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp2s0:
      dhcp4: true
      optional: true
  version: 2
  wifis:
    wlp1s0:
      access-points:
        MYSSID:
          password: ********
      dhcp4: true



```

---

### Post by chili555 on 2022-05-21
Please check the example template at /usr/share/doc/netplan/examples/wireless.yaml. Please double-check all spacing and indentation. Please note that the SSID name and password are enclosed in quotation marks. Please be sure to include renderer: networkd.

---

### Post by mdhankins1 on 2022-05-21
I have done that.  No difference in behavior after a reboot or running netplan apply.  Still not assigned an IP via dhcp.

```

  network:  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      optional: true 
      dhcp4: true
  version: 2
  wifis:
    wlp1s0:
      dhcp4: true
      access-points:
          "MySSID":
            password: "SomePassword"



```

---

### Post by chili555 on 2022-05-21
> NetworkManager: definition enp2s0 is not for us (backend 1)Is this acttually a pure server install? Network Manager, a desktop, etc. are NOT installed, correct?

If NM is installed, you are better off configuring networking there.

---

### Post by mdhankins1 on 2022-05-21
It is a server.  No desktop.  I installed networkmanager because I was hoping I'd have better luck getting the wifi configured using nmcli.  I had already tried configuring wifi using just the netplan file, but as you can see it is not working.

---

### Post by chili555 on 2022-05-21
Let's have a look at:

```
sudo dmesg | grep -e wlp -e iwl
```

---

### Post by mdhankins1 on 2022-05-21
```

root@server1:/etc/netplan# sudo dmesg|grep -e wlp -e iwl
[    9.427429] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    9.435555] iwlwifi 0000:01:00.0: Found debug destination: EXTERNAL_DRAM
[    9.435558] iwlwifi 0000:01:00.0: Found debug configuration: 0
[    9.435703] iwlwifi 0000:01:00.0: loaded firmware version 29.4063824552.0 7265D-29.ucode op_mode iwlmvm
[    9.550578] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    9.567727] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM
[    9.568009] iwlwifi 0000:01:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    9.572887] iwlwifi 0000:01:00.0: base HW address: c0:b6:f9:9d:32:8f
[    9.633303] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.765813] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    9.840964] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM
[    9.926209] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM
[    9.927438] iwlwifi 0000:01:00.0: FW already configured (0) - re-configuring
[  365.832107] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM
[  365.910102] iwlwifi 0000:01:00.0: Applying debug destination EXTERNAL_DRAM
[  365.911391] iwlwifi 0000:01:00.0: FW already configured (0) - re-configuring



```

---

### Post by mdhankins1 on 2022-05-22
Thanks for all the help, but I figured it out.  The problem was my SSID.  When my housemate set it up, they put a space at the end.  Never noticed it until I looked closely at the output of iwlist wlp1s0 scan.  After adding a space to the end of the ssid in my netplan, I was able to connect without a problem.

---

### Post by chili555 on 2022-05-22
Awesome! Glad it's working by whatever means.

---

