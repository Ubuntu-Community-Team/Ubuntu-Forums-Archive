---
title: "Stream bluetooth music to Sony Ericsson MBR-100 music receiver"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by xehapo on 2008-11-27
[B]Hello! I'm trying to stream music from my laptop running Ubuntu 8.10 Intrepid to SE MBR-100 via bluetooth with no luck still.
Generally, the problem is, that hcitool cc drops the connection after it established by unknown reason.
The applet (1.8) fails to establish successful connection, also. I have tried this with two bt usb adapters.
For a part of second something about PIN appears in applet and then connection fails.

here are some outputs:[/B]
hciconfig -a
hci0:	Type: USB
	BD Address: 00:11:67:C1:60:E7 ACL MTU: 1021:4 SCO MTU: 48:10
	UP RUNNING PSCAN ISCAN 
	RX bytes:3583 acl:0 sco:0 events:135 errors:0
	TX bytes:1068 acl:0 sco:0 commands:76 errors:0
	Features: 0xff 0xfe 0xff 0x7e 0x98 0x19 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'barcelona'
	Class: 0x0a010c
	Service Classes: Networking, Capturing
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0x302 LMP Ver: 2.0 (0x3) LMP Subver: 0x302
	Manufacturer: Integrated System Solution Corp. (57)



hcitool cc 00:18:13:DE:8F:55; hcitool info 00:18:13:DE:8F:55
Requesting information ...
	BD Address:  00:18:13:DE:8F:55
	Device Name: MBR-100
	LMP Version: 2.0 (0x3) LMP Subversion: 0xbf1
	Manufacturer: Cambridge Silicon Radio (10)
	Features: 0xff 0xff 0x8f 0x78 0x18 0x18 0x00 0x80
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
		<HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
		<power control> <transparent SCO> <broadcast encrypt> 
		<enhanced iscan> <interlaced iscan> <interlaced pscan> 
		<inquiry with RSSI> <AFH cap. slave> <AFH class. slave> 
		<AFH cap. master> <AFH class. master> <extended features>


**The problem is, that when i do "hcitool cc xx:xx:xx:xx:xx:xx" the connection established first, but it drops a few seconds later**:

root@barcelona:/etc/init.d# hcitool cc 00:18:13:DE:8F:55; hcitool con
Connections:
	< ACL 00:18:13:DE:8F:55 handle 1 state 1 lm MASTER 
root@barcelona:/etc/init.d# hcitool con
Connections:
root@barcelona:/etc/init.d#

**at the same time another terminal session was capturing hcidump:**

hcidump -X -V
HCI sniffer - Bluetooth packet analyzer ver 1.42
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 00:18:13:DE:8F:55 ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 1 bdaddr 00:18:13:DE:8F:55 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 1
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Page Scan Repetition Mode Change (0x20) plen 7
    bdaddr 00:18:13:DE:8F:55 mode 1
> HCI Event: Max Slots Change (0x1b) plen 3
    handle 1 slots 5
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:18:13:DE:8F:55 mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Connection Packet Type Changed (0x1d) plen 5
    status 0x00 handle 1 ptype 0xff1e
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 2-DH1 2-DH3 2-DH5 3-DH1 3-DH3 3-DH5 
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 1
    Features: 0xff 0xff 0x8f 0x78 0x18 0x18 0x00 0x80
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:18:13:DE:8F:55 name 'MBR-100'
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 1 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 1 reason 0x16
    Reason: Connection Terminated by Local Host

[B]

I would like to understand at last, how can I stream the music to my SE MBR-100 device. And cannot understand what the problem happens here, why connection has been dropped, even without PIN request[/B]

**Please help!**

---

### Post by xehapo on 2008-11-28
Got some move since previous post.
With trendnet adapter based on Broadcom chip i got lots of hcidump log for btsco -v xx:xx:xx:xx:xx.
**"btsco -v <mac>"output:**
[FONT="System"]root@barcelona:/usr/sbin# btsco -v 00:18:13:DE:8F:55
btsco v0.42
Device is 2:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Connection refused[/FONT]


**hcidump -X -V:**
[FONT="System"]< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 00:18:13:DE:8F:55 ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr 00:18:13:DE:8F:55 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 12
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 12
    Features: 0xff 0xff 0x8f 0x78 0x18 0x18 0x00 0x80
< ACL data: handle 12 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:18:13:DE:8F:55 mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Max Slots Change (0x1b) plen 3
    handle 12 slots 5
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0000
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0044 scid 0x0040 result 1 status 2
      Connection pending - Authorization pending
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0044 scid 0x0040 result 0 status 0
      Connection successful
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0044 flags 0x00 clen 0
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:18:13:DE:8F:55 name 'MBR-100'
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 48 
< ACL data: handle 12 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0044 flags 0x00 result 0 clen 4
      MTU 48 
< ACL data: handle 12 flags 0x02 dlen 24
    L2CAP(d): cid 0x0044 len 20 [psm 1]
        SDP SSA Req: tid 0x0 len 0xf
          pat uuid-16 0x1108 (Headset)
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
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0044 scid 0x0040
< HCI Command: Read Voice Setting (0x03|0x0025) plen 0
> HCI Event: Command Complete (0x0e) plen 6
    Read Voice Setting (0x03|0x0025) ncmd 1
    status 0x00 voice setting 0x0060
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 3 scid 0x0041
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0045 scid 0x0041 result 1 status 2
      Connection pending - Authorization pending
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0044 scid 0x0040
> HCI Event: Link Key Request (0x17) plen 6
    bdaddr 00:18:13:DE:8F:55
< HCI Command: Link Key Request Reply (0x01|0x000b) plen 22
    bdaddr 00:18:13:DE:8F:55 key 359BE5316A7D74DCE9031DEA115954E3
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Reply (0x01|0x000b) ncmd 1
    status 0x00 bdaddr 00:18:13:DE:8F:55
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0045 scid 0x0041 result 0 status 0
      Connection successful
< ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0045 flags 0x00 clen 4
      MTU 1013 
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 4
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0041 flags 0x00 result 0 clen 0
      Success
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0041 flags 0x00 clen 4
      MTU 1013 
< ACL data: handle 12 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0045 flags 0x00 result 0 clen 4
      MTU 1013 
< ACL data: handle 12 flags 0x02 dlen 8
    L2CAP(d): cid 0x0045 len 4 [psm 3]
      RFCOMM(s): SABM: cr 1 dlci 0 pf 1 ilen 0 fcs 0x1c 
> ACL data: handle 12 flags 0x02 dlen 8
    L2CAP(d): cid 0x0041 len 4 [psm 3]
      RFCOMM(s): UA: cr 1 dlci 0 pf 1 ilen 0 fcs 0xd7 
< ACL data: handle 12 flags 0x02 dlen 18
    L2CAP(d): cid 0x0045 len 14 [psm 3]
      RFCOMM(s): PN CMD: cr 1 dlci 0 pf 0 ilen 10 fcs 0x70 mcc_len 8
      dlci 4 frame_type 0 credit_flow 15 pri 7 ack_timer 0
      frame_size 1008 max_retrans 0 credits 7
> ACL data: handle 12 flags 0x02 dlen 8
    L2CAP(d): cid 0x0041 len 4 [psm 3]
      RFCOMM(s): DM: cr 1 dlci 4 pf 1 ilen 0 fcs 0xbc 
< ACL data: handle 12 flags 0x02 dlen 8
    L2CAP(d): cid 0x0045 len 4 [psm 3]
      RFCOMM(s): DISC: cr 1 dlci 0 pf 1 ilen 0 fcs 0xfd 
< ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0045 scid 0x0041
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 4
> ACL data: handle 12 flags 0x02 dlen 8
    L2CAP(d): cid 0x0041 len 4 [psm 3]
      RFCOMM(s): UA: cr 1 dlci 0 pf 1 ilen 0 fcs 0xd7 
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0045 scid 0x0041
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 1
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 12 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 12 reason 0x16
    Reason: Connection Terminated by Local Host[/FONT]


Does anybody can tell me, how to decrypt this for human beings? :)

Thanks!

---

### Post by xehapo on 2008-11-28
[I]root@barcelona:/usr/sbin# hcitool cc 00:18:13:DE:8F:55
Can't create connection: Input/output error[/I]


and hcidump for this was:
[I]< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 00:18:13:DE:8F:55 ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x04 handle 12 bdaddr 00:18:13:DE:8F:55 type ACL encrypt 0x00
    Error: Page Timeout
[/I]

---

### Post by xehapo on 2008-11-30
Well, I have managed some stability in this bug reproducing and now I have steps to reproduce it with my config.

1. Remove MBR-100 from under btapplet (Right-click on icon in tray->Preferences. Now delete it from the list, using trash bin icon)
2. sudo modprobe bt-sco-snd
3. sudo btsco -v XX:XX:XX:XX:XX:XX

the following hcidump then occured (see attached)

---

### Post by xehapo on 2008-12-02
Dows anynoe has idea how to make Ubuntu stream audio to Bluetooth MBR-100 device?
Did anyone have similar symptoms?

---

### Post by xehapo on 2008-12-03
I have managed the way to workaround this at last! :)

Now I have the following config:
bluez-4.22
bluez-compat-4.22

the following .asoundrc contents:

pcm.btheadset {
type bluetooth
device 00:18:13:DE:8F:55
}

pcm.a2dpd {
          type a2dpd
    }

pcm.bluetuz {
    type plug
    slave {
        pcm btheadset
    }
}

# don't think pcm.a2dpd section is necessary, but, anyway


1. sudo hciconfig hci0 auth
2. sudo modprobe snd-bt-sco; sudo modprobe sco
3. sudo hcitool cc 00:18:13:DE:8F:55
4. sudo pactl load-module module-alsa-sink device=bluetuz
5. sudo pactl load-module module-alsa-source device=bluetuz
6. sudo /etc/init.d/alsa-utils restart

then "sudo cat /proc/asound/cards" will display the lisy of sound devices.
theese devices are bluetooth transport layer redirectors, working on transmitting your sound data to bluetooth streamer. You load them and link to each other in 2nd 4th and 5th steps,
When some applicaton starts audio streaming, the bluetooth connection establishes and the sound starts playing then in couple seconds
After all you can play something using aplay:
aplay -D bluetuz -f S16_LE /destination/to/music/file/file.wav
here bluetuz - is the device name I specified in .asoundrc

I have no idea if it is importrant, but I put two copies under my home directory and root's

Another thing is that there may be some swaps in steps, actually. I have not managed the right command sequence to write a script still, but I will, after my vacation if needed :)

Thanks everybody!

Materials used:
[http://mcmlxxii.co.uk/2008/10/25/amarok-ubuntu-gutsy-bluetooth-and-sony-mbr-100-audio-receiver/](http://mcmlxxii.co.uk/2008/10/25/amarok-ubuntu-gutsy-bluetooth-and-sony-mbr-100-audio-receiver/)
[http://forums.overclockers.com.au/showthread.php?t=694010&page=2](http://forums.overclockers.com.au/showthread.php?t=694010&page=2)
and more more, but those two fit best!

---

