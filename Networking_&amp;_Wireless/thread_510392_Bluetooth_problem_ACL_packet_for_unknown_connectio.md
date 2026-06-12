---
title: "Bluetooth problem: ACL packet for unknown connection handle 11"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by munncha on 2007-07-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110774](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110774) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello, hopefully someone here can help me with this. 

I currently running Ubuntu in VMWare.  I´ve plugged a bluetooth adapter into the VM. I fairly confident all of that is working well. The adapter itself is a cheapo Indian dongle from Inspire HiTech. It declares itself a broadcom one though. I´ve been using the walkthrough at 
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup) 
to generate a serial port from my cellular phone, a t68i. 

However, when attempting to connect to the phone with hcitool cc ADDY i get the following text in my syslogs. 

[ 8545.727641] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8545.776406] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8545.779577] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8545.792639] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8545.797799] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8545.817328] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8545.820407] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 8546.475559] l2cap_recv_acldata: Unexpected continuation frame (len 0)
[ 8546.478452] l2cap_recv_acldata: Unexpected continuation frame (len 0)

The connection command itself silently fails with there being no connection. 

I´ve been poking around trying to determine the source of this and found 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110774](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110774)
[http://canne.wordpress.com/2006/07/10/bluetooth-projects-with-bluez-use-csr-products/](http://canne.wordpress.com/2006/07/10/bluetooth-projects-with-bluez-use-csr-products/)

Which seem to indicate to me that this problem is unsolvable, at least in Ubuntu. 

This dongle works on our windows box so it&#347; going to be hard to justify getting a replacement. I just hoping someone here has some information that would allow me to correct this and use the device correctly. Any advice would be appreciated.

Here&#347; the hciconfig info:
hci0:   Type: USB
        BD Address: 00:08:1B:83:C3:C0 ACL MTU: 1017:8 SCO MTU: 64:0
        UP RUNNING PSCAN ISCAN 
        RX bytes:2745 acl:29 sco:0 events:161 errors:0
        TX bytes:857 acl:0 sco:0 commands:74 errors:0
        Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'ubuntu704desktop-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 2.0 (0x3) HCI Rev: 0x4000 LMP Ver: 2.0 (0x3) LMP Subver: 0x430e
        Manufacturer: Broadcom Corporation (15)

---

