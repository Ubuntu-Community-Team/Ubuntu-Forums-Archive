---
title: "problems with bluetooth and pairing (Samsung E900 and MDA Vario )"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by avdongen on 2007-07-11
Hi,

I am having some problems with pairing my mobile devices. I saw the btproximity monitor on the gentoo wiki and here on th forums and i thought it would be nice to install it on my machine to but i run into some problems.

First of all let me explain what i am using:
[LIST]
[*]Ubuntu Fiesty Fawn
[*]Samsung SGH-E900
[*]T-mobile MDA Vario
[*]Bluetooth USB dongle
[/LIST]

The script didn't work so i tried the step by hand to see where things go wrong. Didn't take long to see that there was no connection being made. I first tried it on the samsung but didn't work at all. Then i tried it with the MDA (which gives responce) but this would also not work.

So let me explain what i did:

First i checked if my bluetooth was up and running:

```

avdongen@Masahiro:~$ hciconfig
       hci0:   Type: USB
        BD Address: 00:10:60:A9:10:28 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:2841 acl:34 sco:0 events:105 errors:0
        TX bytes:1226 acl:33 sco:0 commands:40 errors:0

```

When i try to search for my devices via hidd i get nothing..

```
avdongen@Masahiro:~$ sudo hidd --search
Password:
Searching ...

```
but when i search with the hcitool i find both my phones

```
avdongen@Masahiro:~$ sudo hcitool scan
Scanning ...
        00:12:37:A7:C8:93       Avdongen
        00:17:D5:59:F0:16       Sugoi

```
So my first guess is, there is something wrong when i use hidd so i continue to use hcitool. So next i try to connect to the one of the devices:

```
avdongen@Masahiro:~$ sudo hcitool cc 00:17:D5:59:F0:16
avdongen@Masahiro:~$ sudo hcitool cc 00:12:37:A7:C8:93

```
nothing.. no error, no warning on the either of the phones... so i try hidd to connect:

```
avdongen@Masahiro:~$ sudo hidd --connect 00:17:D5:59:F0:16
avdongen@Masahiro:~$ sudo hidd --connect 00:12:37:A7:C8:93
Can't connect: Connection reset by peer (104)
```

Finally some reaction, the Samsung doesn't do anything but the MDA asks me if my machine is allowed to connect and then asks me for a pin. I enter 1234 (this also the default in in my bluetooth config) but then i get the connection reset by peer error.

Some searching here on the forum and google  suggest that this has something todo with the error:

```
avdongen@Masahiro:~$ hcid -n
hcid[5592]: Bluetooth HCI daemon
hcid[5592]: Could not become the primary owner of org.bluez
hcid[5592]: Unable to get on D-Bus
avdongen@Masahiro:~$ 

```
but there is no real solution to be found anywhere as far as i can see.

Does anyone have a clue whats wrong and how to fix this ?

Regards,

Adrian.

PS this is my hcid.conf

/etc/bluetooth/hcid.conf

```
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
}


```

---

### Post by avdongen on 2007-07-24
This seems to be a known problem.  There is no solution unfortunately so we will have to wait. I tested the same configuration  (phones and USB Bluetooth)  with a clean base install of debian and the problem doesn&#8217;t appear there.

More info:

[http://groups.google.com/group/ubuntu-bluetooth/browse_thread/thread/67032e78137b2d89]("http://groups.google.com/group/ubuntu-bluetooth/browse_thread/thread/67032e78137b2d89")

---

