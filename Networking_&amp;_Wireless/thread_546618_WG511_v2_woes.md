---
title: "WG511 v2 woes"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Maximus.Psychosis on 2007-09-09
OK, I have been reading all the lovely posts out there on this card, I hate being repetitive, but I seem to have an issue with, of course, the connection.  My problem is that even though system can see the AP (Access Point) and the AP can see the card, it cannot establish a connection.

My card (if you haven't guessed) is a  WG511 v2 54MBit/ Wireless PC-Card 88w8335 [Libertas] 802.11b/g Wireless and the AP is a TP-LINK TL-WA501G.

iwconfig:
> 
wlan0     IEEE 802.11b  ESSID:"ap-id"  
                Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
                Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
                RTS thr=2346 B   Fragment thr=2346 B   
                Power Management: off
                Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
               Tx excessive retries:0  Invalid misc:0   Missed beacon:0


the AP info:
> 
ID	MAC Address	             Current Status	       Received Packets	  Sent Packets
1	MA-CF-OR-PO-IN-T1	AP-UP	                         12	                         13450
2       MA-CF-OR-LA-PP-Y1       STA-ASSOC	           12	                           4804


Out of all the wonderful info on the forums, I'm lost and dumbfounded at this, they see yet no talkies (or ping for that matter) so i dint know what to do...

the AP is DHCP'ing, the card don't see a thing of a DHCP sprinkle.... hell have more info:

ifconfig:
> 
wlan0     Link encap:Ethernet  HWaddr  MA-CF-OR-LA-PP-Y1  
          inet6 addr: fe80::214:6cff:fe84:7a02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:28 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:434001 (423.8 KiB)  TX bytes:23938 (23.3 KiB)
          Interrupt:11 Memory:c4010000-c4020000 

wlan0:ava Link encap:Ethernet  HWaddr  MA-CF-OR-LA-PP-Y1
          inet addr:169.254.4.107  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:c4010000-c4020000

ndiswrapper -l
> 
wg511v2 : driver installed
        device (11AB:1FAA) present

iwlist scan:
> 
wlan0     Scan completed :
          Cell 01 - Address: MA-CF-OR-PO-IN-T1
                    ESSID:"ap-id"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          
Cell 02 - Address: MA-CF-OR-PO-IN-T2
                    ESSID:"TP-LINK"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


If anyone has any idea Pleas tell me, I guess I'm a novice at Linux, there's still Heaps of stuff to learn, but I know how to some what root 'n' bash my way in a system... in other words, be gentle :) 

oh, if you want any more info tell me too :P

---

### Post by Maximus.Psychosis on 2007-09-15
Hmm I guess I'll bump this. 

Or if there's no reply after another week, I'll give up on it...

---

### Post by stabbb on 2007-09-20
I also have this card. On edgy it worked via gnome network manager. Everything was fine. After upgrading to feisty it stopped connecting. Ndiswrapper works, card is installed and there is a signal from teh access point. I visited ubuntuguide.org

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_WPA_with_Ndiswrapper_driver]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_WPA_with_Ndiswrapper_driver")

and did what was said there to do. Now it connects but not always. When I turn my laptop on, I open two terminal windows. In the first one I do a 

**ping 192.168.1.1 **

and in the second one I do 

**sudo /etc/init.d/networking restart**

until I see that there's a ping response from the router. I think I should try to install the latest version of ndiswrapper or try one of KDE's wifi apps along with wpa_supplicant, but I'm lazy :P. Hope that helps

---

### Post by Maximus.Psychosis on 2007-09-25
Sweet, now all I need is a AP... where I'm now there's no "Assessable" APs (unless I get the cops on to me) but I could find myself one tonight (and what makes this worse, I'm "inter-tube'less" so I have to get internet access form someone else) so next week ill inform you if it does work, and thank you :)

---

### Post by Maximus.Psychosis on 2007-10-04
Well, i got up to the point of "    * Run the following code to test it and make sure your router is broadcasting its SSID. " and its just dumping errors at me (hell, in the instruction before i wasn't sure if i had to put in the APs SSID (ssid="YourWiFiSSID") or a new one for the card) but it just looped at me with a "State: ASSOCIATING -> DISCONNECTED", so, i have no idea if this thing like my AP, or if kubuntu likes my card... (im almost willing to drip this card for an older 802.11b model from Belkin...

---

### Post by kevdog on 2007-10-04
Take the hyphen out of the ESSID name.  Make sure encryption is off -- it was in the data you presented.

Assuming the ESSID is TPLink, type the following at the command line

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "TPLink"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

---

### Post by Maximus.Psychosis on 2007-10-06
ahh, silly me, should of guessed, well, by assigning my card with an IP and connection to an unencrypted AP i was able to connect, i just have to work out how to go by the encrypted AP that's DHCP'ing...

---

### Post by kevdog on 2007-10-06
Great, is your encrypted access point using WEP or WPA??

---

