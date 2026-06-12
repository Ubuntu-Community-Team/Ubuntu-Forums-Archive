---
title: "Hedgy,  bluez (bluetooth) and KDE"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by uqbar on 2007-01-18
Hi all.
I'm happily running Edgy on my Asus V6J laptop bundled with this BT device:
uqbar@v6j:~$ hciconfig -a hci0
hci0:   Type: USB
        BD Address: 00:15:F2:E7:E7:9D ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:12879 acl:120 sco:0 events:251 errors:0
        TX bytes:3128 acl:118 sco:0 commands:59 errors:0
        Features: 0xff 0xff 0x8b 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'v6j-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 2.0 (0x3) HCI Rev: 0x77b LMP Ver: 2.0 (0x3) LMP Subver: 0x77b
        Manufacturer: Cambridge Silicon Radio (10)

The setup sems to work as my Nokia N70 and the linux box can pair and see each other.
Devices have requested each other the PIN and I've also been able to send a file from the phone to the linux box once I started the obexserver.
The point is that the Kbluetoothd icon in the tray emains grey all the time, except from some blue-flickering during some activitiy. In another KDe based distribution once paired the icon used to stay blue after the pairing.
When I used Konqueror with an sdp:// URL I can see the "service" icons like OBEX File transfer, Dial-Up Networking and so on.
Except that when I click on the OBEX File transfer I switch to an obex://[...]:10/ page with nothing at all inside.
I've tried this command line test:
uqbar@v6j:~$ obexftp -b -l
Scanning ...
Using   00:1A:16:11:xx:xx       Uqbar
Browsing 00:1A:16:11:xx:xx ...
Channel: 10
Connecting...done
Receiving "(null)"... <?xml version="1.0"?>    <!DOCTYPE folder-listing SYSTEM "obex-folder-listing.dtd">    <folder-listing version="1.0"></folder-listing>done
Disconnecting...done

This thing confirms the Konqueror behaviour but says I have nothing to browse on the phone by means of the OBEX protocol.
So I try, from Konqueror, to create a new folder. I get an error dialog box saying "Authentication Required".
This menas I'm missing something. But I don't know what!

Any hint?

If more details are needed, just ask.

Thanks in advance for any kind of help!

---

