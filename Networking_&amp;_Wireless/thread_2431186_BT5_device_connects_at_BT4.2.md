---
title: "BT5 device connects at BT4.2?"
date: 2019-11-12
forum: Networking &amp; Wireless
---

### Post by sremick on 2019-11-12
So I have a set of headphones that are supposedly BT5. They are the Letscom H10: 
[https://www.letscom.com/products/bluetooth-headphones-h10-single/](https://www.letscom.com/products/bluetooth-headphones-h10-single/)

They connect fine to my BT5 card (Intel AX200-based)... however they only connect at BT4.2:

```
$ hcitool info 60:65:19:65:8A:21
Requesting information ...
    BD Address:  60:65:19:65:8A:21
    Device Name: H10
    LMP Version: 4.2 (0x8) LMP Subversion: 0x1450
    Manufacturer: Ceva, Inc. (formerly Parthus Technologies, Inc.) (14)
    Features page 0: 0xff 0xfe 0x8d 0xfa 0xd8 0x3f 0x79 0x87
        <3-slot packets> <5-slot packets> <encryption> <slot offset> 
        <timing accuracy> <role switch> <hold mode> <sniff mode> 
        <RSSI> <channel quality> <SCO link> <HV2 packets> 
        <HV3 packets> <u-law log> <A-law log> <CVSD> <power control> 
        <transparent SCO> <broadcast encrypt> <EDR ACL 2 Mbps> 
        <enhanced iscan> <interlaced iscan> <interlaced pscan> 
        <inquiry with RSSI> <extended SCO> <AFH cap. slave> 
        <AFH class. slave> <LE support> <3-slot EDR ACL> 
        <5-slot EDR ACL> <sniff subrating> <pause encryption> 
        <AFH cap. master> <AFH class. master> <EDR eSCO 2 Mbps> 
        <extended inquiry> <simple pairing> <encapsulated PDU> 
        <err. data report> <non-flush flag> <LSTO> <inquiry TX power> 
        <EPC> <extended features> 
    Features page 1: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00

```

Are these being falsely advertised as BT5, or could I be doing something wrong or missing something?

I'm on Xubuntu 19.10

---

