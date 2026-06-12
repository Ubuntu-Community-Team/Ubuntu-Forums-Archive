---
title: "Need help with bluetooth adaptive frequency hopping configuration"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by hoy_pogi on 2007-10-08
Hi! I'm trying to make my bluetooth dongle avoid channels being used by wifi. I read that the bluetooth 1.2 spec makes use of a technique called adaptive frequency hopping which avoids "busy" frequencies. I'd like to know how to configure this on the command line.

Here's what I've tried so far:

[COLOR="DarkOrange"]-tried using hcitool's get afh channel map parameter:[/COLOR]
hcitool -i hci0 afh 11:11:11:11:11
Get connection info failed: No such file or directory

[COLOR="DarkOrange"]verified BD address (correct)[/COLOR]
hciconfig
hci0:   Type: USB
        BD Address: 11:11:11:11:11:11 ACL MTU: 678:8 SCO MTU: 48:10
        UP RUNNING PSCAN ISCAN 
        RX bytes:2894 acl:0 sco:0 events:52 errors:0
        TX bytes:429 acl:0 sco:0 commands:46 errors:0

[COLOR="DarkOrange"]tried to see what other commands are available for hciconfig[/COLOR]
hciconfig hci0 commands
hci0:   Type: USB
        BD Address: 11:11:11:11:11:11 ACL MTU: 678:8 SCO MTU: 48:10
        Commands: Octet 0  = 0x7f (Bit 0 1 2 3 4 5 6)
                  Octet 1  = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 2  = 0xef (Bit 0 1 2 3 5 6 7)
                  Octet 3  = 0x01 (Bit 0)
                  Octet 4  = 0xfe (Bit 1 2 3 4 5 6 7)
                  Octet 5  = 0xdf (Bit 0 1 2 3 4 6 7)
                  Octet 6  = 0xef (Bit 0 1 2 3 5 6 7)
                  Octet 7  = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 8  = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 9  = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 10 = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 11 = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 12 = 0xf3 (Bit 0 1 4 5 6 7)
                  Octet 13 = 0x0f (Bit 0 1 2 3)
                  Octet 14 = 0xa8 (Bit 3 5 7)
                  Octet 15 = 0xff (Bit 0 1 2 3 4 5 6 7)
                  Octet 16 = 0x07 (Bit 0 1 2)
        'Inquiry' 'Inquiry Cancel' 'Periodic Inquiry Mode' 
        'Exit Periodic Inquiry Mode' 'Create Connection' 'Disconnect' 
        'Add SCO Connection' 'Accept Connection Request' 
        'Reject Connection Request' 'Link Key Request Reply' 
        'Link Key Request Negative Reply' 'PIN Code Request Reply' 
        'PIN Code Request Negative Reply' 'Change Connection Packet Type' 
        'Authentication Requested' 'Set Connection Encryption' 
        'Change Connection Link Key' 'Master Link Key' 'Remote Name Request' 
        'Read Remote Supported Features' 'Read Remote Extended Features' 
        'Read Remote Version Information' 'Read Clock Offset' 'Hold Mode' 
        'Sniff Mode' 'Exit Sniff Mode' 'Park State' 'Exit Park State' 
        'QoS Setup' 'Role Discovery' 'Switch Role' 'Read Link Policy Settings' 
        'Write Link Policy Settings' 'Read Default Link Policy Settings' 
        'Write Default Link Policy Settings' 'Set Event Mask' 'Reset' 
        'Set Event Filter' 'Flush' 'Read PIN Type' 'Write PIN Type' 
        'Read Stored Link Key' 'Write Stored Link Key' 
        'Delete Stored Link Key' 'Write Local Name' 'Read Local Name' 
        'Read Connection Accept Timeout' 'Write Connection Accept Timeout' 
        'Read Page Timeout' 'Write Page Timeout' 'Read Scan Enable' 
        'Write Scan Enable' 'Read Page Scan Activity' 
        'Write Page Scan Activity' 'Read Inquiry Scan Activity' 
        'Write Inquiry Scan Activity' 'Read Authentication Enable' 
        'Write Authentication Enable' 'Read Encryption Mode' 
        'Write Encryption Mode' 'Read Class Of Device' 'Write Class Of Device' 
        'Read Voice Setting' 'Write Voice Setting' 
        'Read Automatic Flush Timeout' 'Write Automatic Flush Timeout' 
        'Read Num Broadcast Retransmissions' 
        'Write Num Broadcast Retransmissions' 'Read Hold Mode Activity' 
        'Write Hold Mode Activity' 'Read Transmit Power Level' 
        'Read Synchronous Flow Control Enable' 
        'Write Synchronous Flow Control Enable' 
        'Set Host Controller To Host Flow Control' 'Host Buffer Size' 
        'Host Number Of Completed Packets' 'Read Link Supervision Timeout' 
        'Write Link Supervision Timeout' 'Read Number of Supported IAC' 
        'Read Current IAC LAP' 'Write Current IAC LAP' 
        'Read Page Scan Period Mode' 'Write Page Scan Period Mode' 
        'Read Page Scan Mode' 'Write Page Scan Mode' 
        'Set AFH Channel Classification' 'Read Inquiry Scan Type' 
        'Write Inquiry Scan Type' 'Read Inquiry Mode' 'Write Inquiry Mode' 
        'Read Page Scan Type' 'Write Page Scan Type' 
        'Read AFH Channel Assessment Mode' 'Write AFH Channel Assessment Mode' 
        'Read Local Version Information' 'Read Local Supported Features' 
        'Read Buffer Size' 'Read Country Code' 'Read BD ADDR' 
        'Read Failed Contact Counter' 'Reset Failed Contact Counter' 
        'Get Link Quality' 'Read RSSI' 'Read AFH Channel Map' 'Read BD Clock' 
        'Read Loopback Mode' 'Write Loopback Mode' 
        'Enable Device Under Test Mode'

[COLOR="DarkOrange"]tried running one of those commands (failed)[/COLOR]
hciconfig hci0 "Set AFH Channel Classification"
hci0:   Type: USB
        BD Address: 11:11:11:11:11:11 ACL MTU: 678:8 SCO MTU: 48:10
        UP RUNNING PSCAN ISCAN 
        RX bytes:2964 acl:0 sco:0 events:53 errors:0
        TX bytes:438 acl:0 sco:0 commands:48 errors:0

[COLOR="DarkOrange"]Tried again, but using hcitool (command line disappeared, can go back by pressing ctrl-c[/COLOR]
sudo hcitool -i hci0 cmd Read Remote Version Information< HCI Command: ogf 0x00, ocf 0x0000, plen 2
  00 00

How exactly do I use hcitool and hciconfig, and how can I change the AFH configuration? I've looked at the manpages, the bluez mailing list, did searches on google, and found no examples of command line parameters for setting AFH configuration.


Thanks

---

