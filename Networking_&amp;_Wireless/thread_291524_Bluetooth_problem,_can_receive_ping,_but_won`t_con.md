---
title: "Bluetooth problem, can receive ping, but won`t connect with rfcomm"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by nick122147 on 2006-11-02
Hi, I`m trying to connect my bluetooth phone.  The phone is discoverd using hcitool scan, and I can ping it and receive reponse, but when I write

sudo rfcomm connect 00:13:70:01:E8:3F 

I get

"Can't connect RFCOMM socket: Host is down"

Any clues on how to get the host up?
if I write hciconfig dev I get

hci0:   Type: USB
        BD Address: 00:02:C7:F9:EE:0B ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:2231 acl:51 sco:0 events:136 errors:0
        TX bytes:1435 acl:55 sco:0 commands:39 errors:0


It seems up and running, so why doesn`t rfcomm want to connnect?

Thanks,

Steinar

---

