---
title: "Palm T3 bluetooth link problems (Gutsy Gibbon)"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by rrottier on 2008-03-17
I am having problems getting my palm T3 connected via bluetooth to my PC.  I tried all the following guides:
[http://ubuntuforums.org/showthread.php?t=113184](http://ubuntuforums.org/showthread.php?t=113184)
[http://ubuntuforums.org/showthread.php?t=374899](http://ubuntuforums.org/showthread.php?t=374899)
[https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)
[http://howto.pilot-link.org/bluesync/index.html](http://howto.pilot-link.org/bluesync/index.html)
and even
[http://forums.fedoraforum.org/archive/index.php/t-2882.html](http://forums.fedoraforum.org/archive/index.php/t-2882.html)

The problem is that the palm just doesn't connect.  I am running Gutsy Gibbon on a IBM T30 with a logitech dongle like descibed in [http://ubuntuforums.org/showthread.php?t=113184](http://ubuntuforums.org/showthread.php?t=113184).

However for some reason whenever I try to connect I get get a error on the palm:"Serial Timeout" and nothing happens on the Laptop.

Please see the output from hcidump pasted below:
HCI sniffer - Bluetooth packet analyzer ver 1.39
device: hci0 snap_len: 1028 filter: 0xffffffff
> HCI Event: Connect Request (0x04) plen 10
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Connect Complete (0x03) plen 11
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
> HCI Event: Max Slots Change (0x1b) plen 3
> HCI Event: Command Status (0x0f) plen 4
< HCI Command: Write Link Policy Settings (0x02|0x000d) plen 4
> HCI Event: Read Remote Supported Features (0x0b) plen 11
> HCI Event: Command Complete (0x0e) plen 6
< HCI Command: Change Connection Packet Type (0x01|0x000f) plen 4
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 0 status 0
      Connection successful
> HCI Event: Command Status (0x0f) plen 4
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
> HCI Event: Connection Packet Type Changed (0x1d) plen 5
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Remote Name Req Complete (0x07) plen 255
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0000 scid 0x0040 result 4 status 0
      Connection refused - no resources available
< ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0040 scid 0x0040
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0000 scid 0x0040 result 4 status 0
      Connection refused - no resources available
< HCI Command: Disconnect (0x01|0x0006) plen 3
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Disconn Complete (0x05) plen 4

Any suggestions would be welcome

---

