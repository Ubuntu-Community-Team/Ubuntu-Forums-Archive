---
title: "Bluetooth: connect: Host is down"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by UbPM on 2015-01-04
I am trying to test *rfcomm_server.c* and *rfcomm_client.c*  (from the link [https://github.com/balle/bluetooth-snippets](https://github.com/balle/bluetooth-snippets)) on my new Bluetooth dongle.

When I run rfcomm_client, it exits on connect giving the error ***"connect: Host is down"***. I am running the client with baddr of hci0.

However, *"hciconfig"* shows the device is up (Mac address changed to XX for the post)

hci0:    Type: BR/EDR  Bus: USB
    BD Address: XX:XX:XX:XX:XX:XX  ACL MTU: 310:10  SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:706 acl:0 sco:0 events:48 errors:0
    TX bytes:1503 acl:0 sco:0 commands:44 errors:0

"hcitool scan" returns the address of one of the paired devices. So I believe the dongle is up. However I am not sure why the connect returns with the Host Down error.

Appreciate any help from the forum.

I am running Ubuntu as a VM on Mac and I have installed "bluez-5.27"

Here are the details of "lsb_release -a"
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

---

