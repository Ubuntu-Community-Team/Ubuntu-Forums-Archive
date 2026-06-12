---
title: "Ubuntu Core 18 - configuring wpa2-enterprise"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by alex-sharaz on 2019-02-04
Hi,
i've installed Ubuntu core 18 on a raspberry pi 3 and am looking to configure eap-tls on its wifi interface.

I've downloaded the classic snap and also the network-manager snap.

The plan is to use nmcli to configure everything along the lines of

nmcli con edit id eduroam

set [FONT=Helvetica]802-1x.ca-cert file /etc/ss/certs//etc/ssl/certs/AddTrust_External_Root.pem[/FONT][FONT=Helvetica] 
[/FONT]set [FONT=Helvetica]802.-1x.client-cert file:// ......
[/FONT]set .. client-key ....
set client-kjey-password .....
set .... wifi-sec key-mgmt wpa-eap


The problem is that from either my login prompt or a sudo'd login prompt whenever I try and specify a certificate file I get a permission denied message. On a snap system how am I supposed to configure stuff using nmcli ? do I have to be in classic to do it ? Having downloaded the network-manager snap its not visible from classic

Rgds
Alex

---

### Post by alex-sharaz on 2019-02-04
o.k. so if i do 
snap info --verbose network-manager

I get 

name:      network-manager
summary:   Network management based on NetworkManager
publisher: Canonical&#10003;
contact:   [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)
license:   unset
description: |
  Network management of wired ethernet, WiFi and mobile data connection based on NetworkManager and
  ModemManager
commands:
  - network-manager.nmcli
services:
  network-manager.networkmanager: simple, enabled, active
notes:
  private:                        false
**  confinement:                    strict**
  devmode:                        false
  jailmode:                       false
  trymode:                        false
  enabled:                        true
  broken:                         false
  ignore-validation:              false
snap-id:      RmBXKl6HO6YOC2DE4G2q1JzWImC04EUy
tracking:     stable
refresh-date: today at 11:03 UTC
channels:
  stable:    1.2.2-22     (383) 4MB -
  candidate: 1.2.2-22     (383) 4MB -
  beta:      1.2.2-22     (383) 4MB -
  edge:      1.2.2-23-dev (386) 4MB -
installed:   1.2.2-22     (383) 4MB

which "...[COLOR=#111111][FONT=Ubuntu]can not access your files, network, processes or any other system resource without requesting specific access via an interface"

So I guess thats why I cannot access te certificates I need for eap-tls

[/FONT][/COLOR]

---

