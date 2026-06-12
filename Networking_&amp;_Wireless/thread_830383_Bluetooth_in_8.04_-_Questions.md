---
title: "Bluetooth in 8.04 - Questions"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by matthewcraig on 2008-06-15
I am going through the steps of getting a new bluetooth keyboard working with 8.04.  I have already seen it working with a seperate linux tablet, so I am sure the hardware works.

First time I have used Bluetooth with Ubuntu, so I am hoping I will be show the light by someone with this post.  I have checked around with the Bluetooth help.ubuntu.com wiki, which was a pretty good help.

I suppose my big question is why the GNOME applets do not show up, when the BT adapter is inserted and when the device pairing occurs.  Shouldn't Ubuntu ask for a pairing code, when hcid.conf is set to "security auto" (default)?

Here are the steps that I have completed in trying to get this BT keyboard paired:

**lsusb**  USB Adapter appears correctly...
```
Bus 001 Device 002: ID 0a5c:2101 Broadcom Corp.
```

**dmesg**  No errors in system log...
```
[11610.010115] usb 1-1: new full speed USB device using ohci_hcd and address 2
[11610.232040] usb 1-1: configuration #1 chosen from 1 choice
```

**hcitool scan**  Device detected correctly...
```
Scanning ...
	00:1E:52:FB:68:44	Apple Wireless Keyboard
```

**sudo hidd --connect 00:1E:52:FB:68:44**
```
Can't create HID control channel: Connection timed out
```

**sudo hidd --search**  Even tried using the alternate meathod...
```
Searching ...
Connecting to device 00:1E:52:FB:68:44
Can't create HID control channel: Connection timed out
```

I have tried to type in the default Ubuntu pairing code (1234 and shift-enter), a different suggested pairing code (0000 and enter), and I have tried not typing anything.  The results are all the same.

Thank you for your consideration.

---

### Post by matthewcraig on 2008-06-15
Tried running hcidump - received the following messages.

```
HCI sniffer - Bluetooth packet analyzer ver 1.40
device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
< HCI Command: Create Connection (0x01|0x0005) plen 13
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Connect Complete (0x03) plen 11
< ACL data: handle 12 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
> HCI Event: Command Status (0x0f) plen 4
< HCI Command: Write Link Policy Settings (0x02|0x000d) plen 4
> HCI Event: Read Remote Supported Features (0x0b) plen 11
> HCI Event: Command Complete (0x0e) plen 6
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0004
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 0 status 0
      Connection successful
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 0
> ACL data: handle 12 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      Success
      MTU 185 
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 185 
< ACL data: handle 12 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      Success
      MTU 185 
< ACL data: handle 12 flags 0x02 dlen 24
    L2CAP(d): cid 0x0040 len 20 [psm 1]
        SDP SSA Req: tid 0x0 len 0xf
          pat uuid-16 0x1200 (PNPInfo)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 00
> HCI Event: Number of Completed Packets (0x13) plen 5
> ACL data: handle 12 flags 0x02 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 19
    L2CAP(d): cid 0x0040 len 96 [psm 1]
        SDP SSA Rsp: tid 0x0 len 0x5b
          count 88
          record #0
              aid 0x0000 (SrvRecHndl)
                 uint 0x10001
              aid 0x0001 (SrvClassIDList)
                 < uuid-16 0x1200 (PNPInfo) >
              aid 0x0004 (ProtocolDescList)
                 < < uuid-16 0x0100 (L2CAP) uint 0x1 > <
                 uuid-16 0x0001 (SDP) > >
              aid 0x0009 (BTProfileDescList)
                 < < uuid-16 0x1200 (PNPInfo) uint 0x100 > >
              aid 0x0200 (VersionNumList)
                 uint 0x100
              aid 0x0201 (SrvDBState)
                 uint 0x5ac
              aid 0x0202 (unknown)
                 uint 0x22c
              aid 0x0203 (unknown)
                 uint 0x136
              aid 0x0204 (unknown)
                 bool 0x1
              aid 0x0205 (unknown)
                 uint 0x2
          cont 00
< ACL data: handle 12 flags 0x02 dlen 24
    L2CAP(d): cid 0x0040 len 20 [psm 1]
        SDP SSA Req: tid 0x1 len 0xf
          pat uuid-16 0x1124 (HID)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 00
> ACL data: handle 12 flags 0x02 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 24
    L2CAP(d): cid 0x0040 len 128 [psm 1]
        SDP SSA Rsp: tid 0x1 len 0x7b
          count 118
          cont 02 00 76
< ACL data: handle 12 flags 0x02 dlen 26
    L2CAP(d): cid 0x0040 len 22 [psm 1]
        SDP SSA Req: tid 0x2 len 0x11
          pat uuid-16 0x1124 (HID)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 02 00 76
> ACL data: handle 12 flags 0x02 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 24
    L2CAP(d): cid 0x0040 len 128 [psm 1]
        SDP SSA Rsp: tid 0x2 len 0x7b
          count 118
          cont 02 00 EC
< ACL data: handle 12 flags 0x02 dlen 26
    L2CAP(d): cid 0x0040 len 22 [psm 1]
        SDP SSA Req: tid 0x3 len 0x11
          pat uuid-16 0x1124 (HID)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 02 00 EC
> HCI Event: Number of Completed Packets (0x13) plen 5
> ACL data: handle 12 flags 0x02 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 24
    L2CAP(d): cid 0x0040 len 128 [psm 1]
        SDP SSA Rsp: tid 0x3 len 0x7b
          count 118
          cont 02 01 62
< ACL data: handle 12 flags 0x02 dlen 26
    L2CAP(d): cid 0x0040 len 22 [psm 1]
        SDP SSA Req: tid 0x4 len 0x11
          pat uuid-16 0x1124 (HID)
          max 65535
          aid(s) 0x0000 - 0xffff
          cont 02 01 62
> ACL data: handle 12 flags 0x02 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 27
> ACL data: handle 12 flags 0x01 dlen 1
    L2CAP(d): cid 0x0040 len 78 [psm 1]
        SDP SSA Rsp: tid 0x4 len 0x49
          count 70
          record #0
              aid 0x0000 (SrvRecHndl)
                 uint 0x10000
              aid 0x0001 (SrvClassIDList)
                 < uuid-16 0x1124 (HID) >
              aid 0x0004 (ProtocolDescList)
                 < < uuid-16 0x0100 (L2CAP) uint 0x11 > <
                 uuid-16 0x0011 (HIDP) > >
              aid 0x0005 (BrwGrpList)
                 < uuid-16 0x1002 (PubBrwsGrp) >
              aid 0x0006 (LangBaseAttrIDList)
                 < uint 0x656e uint 0x6a uint 0x100 >
              aid 0x0009 (BTProfileDescList)
                 < < uuid-16 0x1124 (HID) uint 0x100 > >
              aid 0x000d (IconURL)
                 < < < uuid-16 0x0100 (L2CAP) uint 0x13 > < uuid-16 0x0011 (HIDP) > > >
              aid 0x0100 (SrvName)
                 str "Apple Wireless Keyboard"
              aid 0x0101 (SrvDesc)
                 str "Keyboard"
              aid 0x0102 (ProviderName)
                 str "Apple Inc."
              aid 0x0201 (SrvDBState)
                 uint 0x111
              aid 0x0202 (unknown)
                 uint 0x40
              aid 0x0203 (unknown)
                 uint 0x21
              aid 0x0204 (unknown)
                 bool 0x1
              aid 0x0205 (unknown)
                 bool 0x1
              aid 0x0206 (unknown)
                 < < uint 0x22 str 05 01 09 06 a1 01 85 01 05 07 19 e0 29 e7 15 00 25 01 75 01 95 08 81 02 75 08 95 01 81 01 75 01 95 05 05 08 19 01 29 05 91 02 75 03 95 01 91 01 75 08 95 06 15 00 26 ff 00 05 07 19 00 2a ff 00 81 00 c0 05 0c 09 01 a1 01 85 47 05 01 09 06 a1 02 05 06 09 20 15 00 26 ff 00 75 08 95 01 81 02 c0 c0 05 0c 09 01 a1 01 85 11 15 00 25 01 75 01 95 03 81 01 75 01 95 01 05 0c 09 b8 81 02 06 ff 00 09 03 81 02 75 01 95 03 81 01 05 0c 85 12 15 00 25 01 75 01 95 01 09 cd 81 02 09 b3 81 02 09 b4 81 02 09 b5 81 02 09 b6 81 02 81 01 81 01 81 01 85 13 15 00 25 01 75 01 95 01 06 01 ff 09 0a 81 02 75 01 95 07 81 01 c0 > >
              aid 0x0207 (unknown)
                 < < uint 0x409 uint 0x100 > >
              aid 0x020b (unknown)
                 uint 0x100
              aid 0x020c (unknown)
                 uint 0xc80
              aid 0x020d (unknown)
                 bool 0x1
              aid 0x020e (unknown)
                 bool 0x1
          cont 00
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0040 scid 0x0040
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0040 scid 0x0040
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 17 scid 0x0040
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0041 scid 0x0040 result 1 status 0
      Connection pending - No futher information available
> HCI Event: Number of Completed Packets (0x13) plen 5
> HCI Event: PIN Code Request (0x16) plen 6
< HCI Command: Disconnect (0x01|0x0006) plen 3
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Disconn Complete (0x05) plen 4
```

You'll see at the fourth-to-last line the PIN Code Request when I tried using '1234 then shift-enter', so I know the pairing code is being received.  If I instead try no code, then that line is omitted and the disconnect happens the same way.  Anyone know what these "plen" codes mean?  Anyway, I do not see any errors.

---

### Post by matthewcraig on 2008-06-15
I played around with the settings a bit more based on the HOWTO which I [found here]("http://ubuntuforums.org/showthread.php?t=224673").  It recommended logging out and logging back in again, which I believe helped.

Now, the trace says the following, when I type a pairing code in the BT keyboard.  Could there be a GNOME issue?  Because I see nothing pop-up asking me to confirm the code.

```
> HCI Event: PIN Code Request (0x16) plen 6
< HCI Command: PIN Code Request Negative Reply (0x01|0x000e) plen 6
> HCI Event: Command Complete (0x0e) plen 10
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0000 scid 0x0040 result 3 status 0
      Connection refused - security block
> HCI Event: Disconn Complete (0x05) plen 4
```

The hidd --connect immediately terminates with an error, when the code is entered on the BT keyboard.  Even a debug trace gives little insight into the problem.

---

### Post by matthewcraig on 2008-06-15
Giving up for now.  I suspect the issue is raising the pop-up in GNOME to solicit the pair code response.  Why this desktop function isn't working, I have no idea.  Hope this information helps someone else fighting through the same thing.

---

### Post by matthewcraig on 2008-06-23
Huzzah!  I am writing this from my BT keyboard.  The issue was the Gnome Applet.  When I looked into the Gnome "Sessions" menu, I saw it was not 'checked' in order to start up upon login.  I ran "bluetooth-applet" and I tried the --connect command again.  This time, with the BT applet running, a pop-up displayed asking for confirmation of the pairing code.  Indeed, my suspicions were correct, the security error was the Bluez Tools not being authorized for the pop-up.  Now, the applet has the pairing showns as a "lock icon", so this should work automagically, now.

If anyone else sees that the "bluetooth-applet" does not configure itself to run at login, then it is probably a bug and it should be filed in Launchpad, as such.

---

