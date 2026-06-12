---
title: "Bluetooth has to be configured on each start-up"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by Grizzlitiger on 2006-08-20
Hello there,

after meticulously following the instruction on how to set up bluetooth under ubuntu linux on [http://wiki.ubuntuusers.de/Bluetooth_Headset](http://wiki.ubuntuusers.de/Bluetooth_Headset) I finally managed to get it working. :-D 
However, the problem is, that I apparently have to re-pair the headset and my laptop on each start-up. I dual-boot and so I have to do this under both windows and linux. ](*,)  Is there a way to avoid this?
Furthermore I have to re-configure bluetooth on each start-up with ubuntu. If I don't, I get - trying to connect with btsco -v MACADRESSOFTHEBLUETOOTHDEVICE - the error message:

btsco v0.4c
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied

And it only works if I delete /var/lib/bluetooth/MACADRESSOFTHEBLUETOOTHDEVICE and then restart the bluetooth services with sudo /etc/init.d/bluez-utils restart and only after doing that I can finally connect again with btsco -v MACADRESSOFTHEBLUETOOTHDEVICE.

Btw: Of what use exactly is the gnome bluetooth manager? Because it was, as far as I can tell, no help in setting up bluetooth.

I realise my describitions are a bit confusing in some parts and I apologise for that, however, I would greatly appreciate any help and thank all of you in advance!

Greetings,
Grizzlitiger

---

### Post by mlind on 2006-08-20
This wiki article has something about pairing devices on startup
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

It doesn't use btsco, so I don't know if it'll be any help.

About gnome-bluetooth, I think it's currently only useful for OBEX object sending/serving (file transfers between devices). It's not very useful for pairing..

You could install bluez-hcidump, and run hcidump -V -X to get the idea what's going on.

---

### Post by Grizzlitiger on 2006-08-21
Thanks very much for you advice!

Um unfortunately I haven't been able to hidd, it does not detect my bluetooth device (headset) in the first place, it says 

Searching ...
        No devices in range or visible
when the headset is not in pairing mode, when in pairing mode it doesn't say anything,
nor does it connect to it, when given the  mac address. It says 

jmoeller@JSM:~$ sudo hidd --connect 00:0D:44:5C:18:E5
Password:
Can't get device information: Success

bluez-hcidump works with sudo. Since I don't know how to exactly interpret the output I thought it prduent to post it here: When connected I get this, e.g.:

SCO data: handle 1 dlen 48
    0000: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
    0010: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
    0020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................

and this when not connected, i.e. when I want to connect:
```
jmoeller@JSM:~$ sudo hcidump -V -X
HCI sniffer - Bluetooth packet analyzer ver 1.28
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 00:0D:44:5C:18:E5 ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Link Key Request (0x17) plen 6
    bdaddr 00:0D:44:5C:18:E5
< HCI Command: Link Key Request Reply (0x01|0x000b) plen 22
    bdaddr 00:0D:44:5C:18:E5 key 571CB4A785FE0070FAC467BE5720136F
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Reply (0x01|0x000b) ncmd 1
    status 0x00 bdaddr 00:0D:44:5C:18:E5
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr 00:0D:44:5C:18:E5 type ACL encrypt 0x01
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
< HCI Command: Write Link Policy Settings (0x02|0x000d) plen 4
    handle 12 policy 0x0f
    Link policy: RSWITCH HOLD SNIFF PARK
> HCI Event: Command Complete (0x0e) plen 6
    Write Link Policy Settings (0x02|0x000d) ncmd 1
    status 0x00 handle 12
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0047 scid 0x0040 result 1 status 2
      Connection pending - Authorization pending
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0047 scid 0x0040 result 0 status 0
      Connection successful
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0047 flags 0x00 clen 0
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 48
< ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0047 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 12 flags 0x02 dlen 24
    L2CAP(d): cid 0x0047 len 20 [psm 1]
        SDP SSA Req: tid 0x0 len 0xf
          pat uuid-16 0x1200 (PNPInfo)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 00
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 4
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(d): cid 0x0040 len 10 [psm 1]
        SDP SSA Rsp: tid 0x0 len 0x5
          count 2
          cont 00
< ACL data: handle 12 flags 0x02 dlen 24
    L2CAP(d): cid 0x0047 len 20 [psm 1]
        SDP SSA Req: tid 0x1 len 0xf
          pat uuid-16 0x1124 (HID)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 00
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(d): cid 0x0040 len 10 [psm 1]
        SDP SSA Rsp: tid 0x1 len 0x5
          count 2
          cont 00
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0047 scid 0x0040
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0047 scid 0x0040
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0048 scid 0x0040 result 1 status 2
      Connection pending - Authorization pending
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0048 scid 0x0040 result 0 status 0
      Connection successful
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0048 flags 0x00 clen 0
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 4
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 48
< ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0048 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 12 flags 0x02 dlen 22
    L2CAP(d): cid 0x0048 len 18 [psm 1]
        SDP SSA Req: tid 0x0 len 0xd
          pat uuid-16 0x1108 (Headset)
          max 65535
          aid(s) 0x0004 (ProtocolDescList)
          cont 00
> ACL data: handle 12 flags 0x02 dlen 27
> ACL data: handle 12 flags 0x01 dlen 8
    L2CAP(d): cid 0x0040 len 31 [psm 1]
        SDP SSA Rsp: tid 0x0 len 0x1a
          count 23
          record #0
              aid 0x0004 (ProtocolDescList)
                 < < uuid-16 0x0100 (L2CAP) > <
                 uuid-16 0x0003 (RFCOMM) uint 0x1 > >
          cont 00
< ACL data: handle 12 flags 0x02 dlen 22
    L2CAP(d): cid 0x0048 len 18 [psm 1]
        SDP SSA Req: tid 0x1 len 0xd
          pat uuid-16 0x1101 (SP)
          max 65535
          aid(s) 0x0004 (ProtocolDescList)
          cont 00
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(d): cid 0x0040 len 10 [psm 1]
        SDP SSA Rsp: tid 0x1 len 0x5
          count 2
          cont 00
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0048 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 4
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0048 scid 0x0040
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 12 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 12 reason 0x16
    Reason: Connection Terminated by Local Host
< HCI Command: Inquiry (0x01|0x0001) plen 5
    lap 0x9e8b33 len 8 num 0
> HCI Event: Command Status (0x0f) plen 4
    Inquiry (0x01|0x0001) status 0x00 ncmd 1
> HCI Event: Inquiry Complete (0x01) plen 1
    status 0x00

```

Maybe this has got something to do with the key that is generated while pairing but why should it be necessary to create a new one each time I restart the bluetooth device on my laptop (as I said, I always have to delete /var/lib/bluetooth/MACADDRESS)? Btw. is there a way to make it (the key) accesible to both windows and ubuntu?

Thanks for any help!
Edit: The described way to connect at startup automatically doesn't work either.

---

### Post by mlind on 2006-08-21
The problem is probaby with /var/lib/bluetooth/<hwaddr>/linkkeys file. I guess it's generated after two devices have been paired, but for some reason connecting devices second time fails (even though already paired).

Does your /etc/bluetooth/hcid.conf contain
```

# Authentication and Encryption (Security Mode 3)
      #auth enable;
      #encrypt enable;

```

So that both are disabled? And your headset is not on pairing mode when you connect?

---

### Post by Grizzlitiger on 2006-08-21
Hello,

yes /etc/bluetooth/hcid.conf contains exactly the lines you quoted. The headset has to be in pairing mode for hcitool to be able to detect it. However, the headset is not in pairing mode when I connect.

Thanks for your help!

[B]EDIT
THE SOLUTION?[/B]
ok the problem probably is as follows:

i pair successfully my headset with ubuntu and thereby generate a key. however, if i switch to windows windows has another key for that headset and forces to re-pair und generate a new one. this new key is not available for linux either, so i got a problem. by deleting /var/lib/bluetooth/MACADD i delete the key linux would use and force it to re-pair and generate a new one. a possible solution would - if this is correct - to somehow share the key between linux and windows. so my question is, since i haven't yet been able to find the answer, where does the ibm thinkpad bluetooth tool store its pairing key? i already found a file called BTKeyInd.dll. which is in the bluetooth folder. this may be the right one but with linux i can't access it and with windows wordpad it's all gibberish.
any ideas?
:?:

---

