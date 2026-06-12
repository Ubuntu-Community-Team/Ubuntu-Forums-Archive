---
title: "rfcomm release and rfcomm connect, can it be done automatically? please help"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by mike.thorton on 2007-02-08
Hello,

please help me. Sometimes I need to connect to my Nokia 6230i via bluetooth. I have already managed to do this, but I have to do:
```
rfcomm connect 0
```

and what is worse, after reboot I have to do:
```
sudo rfcomm release /dev/rfcomm0
rfcomm connect 0

```

because rfcomm connect 0 returns
*Can't connect RFCOMM socket: Device or resource busy*


Then I'm able to connect to Internet with
```
pppd call gprs
```

Can anybody help me, how to release automatically? Connecting is also annoying, I would like to connect every time my phone is "available" - bluetooth is turned on on my mobile.

Here you are my conf files:
```
cat /etc/bluetooth/hcid.conf
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
        pin_helper /usr/bin/bluepin;

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

```

```

cat /etc/bluetooth/rfcomm.conf
#
# RFCOMM configuration file.

rfcomm0 {
         bind no;
         device 00:12:D2:CD:AD:9E;
         channel 1;
         comment "Nokia";
 }

```

I use Ubuntu 6.06 LTS with Gnome, I have bluez-utils installed, my laptop is nx6110 but I don't know how to discover what bluetooth module I have.

Thank you for your replies!

---

### Post by glabouni on 2007-02-23
you might want to try to change 

```
rfcomm0 {
       bind no;
```

to

```
rfcomm0 {
#       # Automatically bind the device at startup
       bind yes;
```
btw, can you describe what steps you went through to get ubuntu working with a nokia 6230i via bluetooth ?

I'm currently using edgy, at first the phone detected the computer and connection always failed rejecting the PIN for some reason. 
So I tried my luck with gammu and wammu, but the package available in repositories are so old that I decided to compile the most recent ones (which happens to be a few hours old). 

now gammu and wammu raise an unknown OS error, and the 6230i doesn't detect the computer anymore.

---

