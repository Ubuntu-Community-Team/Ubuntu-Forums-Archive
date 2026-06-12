---
title: "gnome obex server cannot open display."
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by electroconvulsive on 2007-05-12
Hi I'm trying to get my bluetooth networking happening with my install of Ubuntu Feisty. when I click on the Bluetooth File Sharing panel under accessories nothing happens. I tried using the command gnome-obex-server in the terminal and got the following reply.
```
(gnome-obex-server:10551): Gtk-WARNING **: cannot open display:
```
I looked at a few other threads on these forums and got an idea of what to enter into terminal to see what was going on. I don't really have much of a clue about this stuff but I hope that this information is useful to someone a little more knowledgeable than me.

First I tried lsusb and it gave me the following output.
```
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04d9:0024 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
Next I tried to query my phone in  the terminal by using hcitool inq and it returned ```
 Inquiring ...
        00:0E:ED:E1:BC:A7       clock offset: 0x4ce5    class: 0x520204
``` Then I tried using hcitool dev and was returned the following code. ```
Devices:
        hci0    00:13:85:00:0D:5A
```
Next I looked at the output of /etc/default/bluetooth. I have only  included the lines that arent commented out here.```
BLUETOOTH_ENABLED=1
HIDD_ENABLED=0
HIDD_OPTIONS="--master --server"
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
DUND_ENABLED=0
DUND_OPTIONS="--listen --persist"
PAND_ENABLED=0
PAND_OPTIONS=""
SDPTOOL_OPTIONS=""
```
Next I looked at  /etc/bluetooth/hcid.conf```
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
        security user;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        passkey "1234";
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
        discovto 0;

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

```
Im not really sure what else to look for or why it isnt working so I hope that a person of wisdom may be able to help here.

Thanks in advance.

---

