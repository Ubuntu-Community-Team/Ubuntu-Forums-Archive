---
title: "Bluetooth card detected, but can't detect my phone and vice versa"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by Nanoboy on 2007-07-08
The built-in bluetooth card is detected as I did *sudo hciconfig -a* showed:
```
jack@hedgehog:~$ sudo hciconfig -a
hci0:   Type: USB
        BD Address: 00:10:C6:4E:07:51 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:1196 acl:0 sco:0 events:52 errors:0
        TX bytes:658 acl:0 sco:0 commands:40 errors:0
        Features: 0xff 0xff 0x8f 0x78 0x18 0x18 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'hedgehog-0'
        Class: 0x3e010c
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Laptop
        HCI Ver: 1.2 (0x2) HCI Rev: 0x4f2 LMP Ver: 1.2 (0x2) LMP Subver: 0x4f2
        Manufacturer: Cambridge Silicon Radio (10)

```
I have installed all the bluetooth, bluez and obex and the related python packages.

I could turn my bluetooth on and off by the Fn + F2 keys as my bluetooth manager icon indicated.

But I could never detect any bluetooth devices by scanning:
```
jack@hedgehog:~$ hcitool scan
Scanning ...
jack@hedgehog:~$ 

```

And I think the following outcome seems wrong as well:
```
jack@hedgehog:~$ sudo hcitool inq
Password:
Inquiring ...
jack@hedgehog:~$ 

```

Tried the following, didn't work either:
```
jack@hedgehog:~$ sudo hciconfig hci0 reset
jack@hedgehog:~$ hidd --searchSearching ...
        No devices in range or visible
jack@hedgehog:~$ 

```

No joy at all!!  :(

I agree with the sentiments from this thread [[COLOR="Blue"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=444233")
that the uneasy installation of bluetooth in Ubuntu is really killing!!

---

### Post by michelino on 2007-08-23
I'm in the same situation with a different bluetooth chipset:
```
hciconfig -a 
hci0:   Type: USB
        BD Address: 00:16:41:1B:97:A3 ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN 
        RX bytes:5512 acl:0 sco:0 events:302 errors:0
        TX bytes:1937 acl:0 sco:0 commands:96 errors:0
        Features: 0xff 0xff 0x9f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'michele-p-0'
        Class: 0x3e010c
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Laptop
        HCI Ver: 1.2 (0x2) HCI Rev: 0x679 LMP Ver: 1.2 (0x2) LMP Subver: 0x679
        Manufacturer: Cambridge Silicon Radio (10)
```
Any suggestions?

---

