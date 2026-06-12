---
title: "Mobile Phone can't connect to the Computer use Bluetooth"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by AnThOnYhO on 2007-05-22
My computer can send the file to Mobile phone use the BT dongle.
But use the phone i will find the computer but can't pair it.
The hcid -n report:
hcid[5674]: Bluetooth HCI daemon
hcid[5674]: Could not become the primary owner of org.bluez
hcid[5674]: Unable to get on D-Bus

My hcid.conf


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
        security none;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;
        
        # Default PIN code for incoming connections
        passkey "0000";
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
        discovto 1;

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
}


And  the rfcomm.conf


#
# RFCOMM configuration file.
#

#rfcomm0 {
#       # Automatically bind the device at startup
#       bind no;
#
#       # Bluetooth address of the device
#       device 11:22:33:44:55:66;
#
#       # RFCOMM channel for the connection
#       channel 1;
#
#       # Description of the connection
#       comment "Example Bluetooth device";
#}
rfcomm0 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 00:15:2A:41:7D:D4;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "Nokia 3230";
}

As i think maybe it is a pin_helper question.
Under feisty os

---

### Post by AnThOnYhO on 2007-05-22
Someone  can help me.

---

