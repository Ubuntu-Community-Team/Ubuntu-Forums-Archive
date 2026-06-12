---
title: "bluetooth adapter (cc3023) not working on toshiba m30x-165 with ubuntu dapper"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by nab on 2007-02-05
Hi all,

I try to get my bluetooth adapter anycom usb-200 (cc3023) working on a toshiba m30x-165 notebook with ubuntu dapper and to connect to  logitech mobile freedom headset (version 1.2).


Following this howto [http://wiki.ubuntuusers.de/Bluetooth/Einrichtung](http://wiki.ubuntuusers.de/Bluetooth/Einrichtung)

I have following packages installed:
- bluez-utils
- bluez-btsco
- bluez-pin
- libopenobex-1.0-0
- qobex
- libbluetooth1

With "sudo /etc/init.d/bluez-utils restart" I restarted the bluetooth services.

With "lsusb" I get following output:

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp.
Bus 003 Device 003: ID 0a5c:2111 Broadcom Corp.
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

So I think the stick is recognised.

With "hciconfig -a" I see the first signs of troubles:

hci0:   Type: USB
        BD Address: 00:16:38:CA:69:BC ACL MTU: 1017:8 SCO MTU: 64:1
        UP RUNNING
        RX bytes:171 acl:0 sco:0 events:25 errors:0
        TX bytes:603 acl:0 sco:0 commands:25 errors:0
        Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
Can't read local name on hci0: Input/output error (5)

with "hciconfig hci0 revision" I get:

hci0:   Type: USB
        BD Address: 00:16:38:CA:69:BC ACL MTU: 1017:8 SCO MTU: 64:1
        Firmware 8494.65 / 128

Changing the usb port and restarting doesn't change the output.

I put the pin code of the headset in /etc/bluetooth/pin in plain text.

I didn't change anything in /etc/bluetooth/hcid.conf

#
# HCI daemon configuration file.
#

# HCId options
options {
   # Automatically initialize new devices
   autoinit yes;

   # Security Manager mode
   #   none - Security manager disabled
   #   auto - Use local PIN for incoming connections
   #   user - Always ask user for a PIN
   #
   security auto;

   # Pairing mode
   #   none  - Pairing disabled
   #   multi - Allow pairing with already paired devices
   #   once  - Pair once and deny successive attempts
   pairing multi;

   # PIN helper
        #    /usr/bin/pinwrapper
        #    /usr/bluez-pin
   pin_helper /usr/bin/pinwrapper;

   # D-Bus PIN helper
   #dbus_pin_helper;
}

# Default settings for HCI devices
device {
   # Local device name
   #   %d - device id
   #   %h - host name
   name "%h-%d";

   # Local device class
   class 0x3e0100;

   # Default packet type
   #pkt_type DH1,DM1,HV1;

   # Inquiry and Page scan
   iscan enable; pscan enable;

   # Default link mode
   #   none   - no specific policy
   #   accept - always accept incoming connections
   #   master - become master on incoming connections,
   #            deny role switch on outgoing connections
   lm accept;

   # Default link policy
   #   none    - no specific policy
   #   rswitch - allow role switch
   #   hold    - allow hold mode
   #   sniff   - allow sniff mode
   #   park    - allow park mode
   lp rswitch,hold,sniff,park;

   # Authentication and Encryption (Security Mode 3)
   #auth enable;
   #encrypt enable;
}

Do I have to change the class?
Or is my adapter defect?

With "hcitool scan" I tried to find my headset (logitech mobile freedom) without success "Inquiry failed: Connection timed out".

Well not being an linux expert I don't know how to continue.
Any help is greatly appriciated.

TIA
Nikolaus

---

### Post by nab on 2007-02-09
Hi all,

I got help on another forum :-) und thought to present the solution here:

Running "hciconfig hci0 reset" after plugging the dongle in worked.

Nikolaus

---

