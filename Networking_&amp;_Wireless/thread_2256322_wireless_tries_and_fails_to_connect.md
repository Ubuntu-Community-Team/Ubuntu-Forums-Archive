---
title: "wireless tries and fails to connect"
date: 2014-12-11
forum: Networking &amp; Wireless
---

### Post by NyteRukh on 2014-12-11
I had to reset my cable modem this morning...and the laptop no longer connects to the internet..even though it see's and tries to connect. I had to originally use the work around found here for the Asus x551ma laptop...and it worked fine..till this morning..here are the results of some command i was told to run.

lspci -nn | grep 0280
  02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

wlan0   14 channels in total; available frequencies :
      channel 1: 2.412 GHz
      channel 2: 2.417 GHz
      channel 3: 2.422 ghz
      channel 4: 2.427 ghz
      channel 5: 2.432 ghz
      channel 6: 2.437 ghz
      channel 7: 2.442 ghz
      channel 8: 2.447 ghz
      channel 9: 2.452 ghz
      channel 10: 2.457 ghz
      channel 11: 2.462 ghz
      channel 12: 2.467 ghz
      channel 13: 2.472 ghz
      channel 14: 2.484 ghz

sudo iwlist wlan0 scan


wlan0     Scan completed :
          Cell 01 - Address: 90:48:9A:5A:30:EC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"DVW3201B7F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000141d44ff4a8
                    Extra: Last beacon: 896ms ago
                    IE: Unknown: 000A44565733323031423746
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010161BBE5F831A66E2D6BB5CCCE5CBF079102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203000C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 02 - Address: B0:A7:37:13:52:13
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-559-03DB9C"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000484a3d790
                    Extra: Last beacon: 848ms ago
                    IE: Unknown: 00164449524543542D726F6B752D3535392D303344423943
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ABC1916FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD090010180200004C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DDAE0050F204104A0001101044000102103B0001031047001022210203040506070809B0A73713521310210004526F6B7510230014526F6B752053747265616D696E6720537469636B1024001833353030582076657220352E36206275696C6420323034371042000C324C2A2A2A2A2A2A2A3535391054000800060050F2040001101100164449524543542D726F6B752D3535392D303344423943100800020000103C0001011049000600372A000120
                    IE: Unknown: DD16506F9A0A00000600111C4400960A0006B2A737135211
          Cell 03 - Address: 00:00:00:00:00:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"JRLeimer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ca5e0740
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 00084A524C65696D6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010F239EB3CA7EC51ED502FA429356E0780102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180204001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:1E:2A:69:46:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"RIGIDCHOPPER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000098fa244469
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000C524947494443484F50504552
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F0201010D0002A44000
                    IE: Unknown: DD1A00037F0301000000001E2A69465E021E2A69465E64002C011D08
          Cell 05 - Address: 14:2D:27:6F:02:3E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"JRLeimer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ca5ccf33
                    Extra: Last beacon: 928ms ago
                    IE: Unknown: 00084A524C65696D6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180204001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by chili555 on 2014-12-11
I assume this is your network:> Cell 05 - Address: 14:2D:27:6F:02:3E
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=46/70 Signal level=-64 dBm 
Encryption key:on
ESSID:"JRLeimer"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:MasterFirst, you say you reset your modem; I'm not sure what you mean by that. Do you mean that you changed a setting or two in the modem? Or do you mean that you simply rebooted the modem and no more?

If you made some changes, I'd click the Network Manager icon, edit connections and delete the network altogether. Then restart NM:```
sudo service network-manager restart
```NM should then report that networks are available; select yours, supply the WPA2 password and try to connect.

---

### Post by NyteRukh on 2014-12-11
i meant that i simply turned the modem off then on

Ok here's what i did. i reinstalled ubuntu 14.1 on the laptop, and downloaded all updates and got to laptop situated where i liked it...to do that i had to connect to the internet using my wireless usb stick. after i got everything situated where i liked it i went to the asus wifi disabled (hard-blocked) post and followed the directions as what to do to fix the problem. this time it didnt even work. the system see's and tries to connect using the onboard wifi.but wont connect (forcing me to go back to the wifi stick. I even installed the xbindkeys part and set up to the toggle. but no go...im at a total loss as to what to do. here is some of the outputs of various commands.

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

iwconfig

eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:"JRLeimer"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 14:2D:27:6F:02:3E   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retryoff   RTS thr:off   Fragment thr:off
          Power Managementoff
          Link Quality=100/100  Signal level=90/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig

eth0      Link encap:Ethernet  HWaddr e0:3f:49:c2:0f:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31702 (31.7 KB)  TX bytes:31702 (31.7 KB)


wlan0     Link encap:Ethernet  HWaddr 54:27:1e:20:69:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan1     Link encap:Ethernet  HWaddr b4:75:0e:7a:79:99  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b675:eff:fe7a:7999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2962 errors:0 dropped:391 overruns:0 frame:0
          TX packets:2213 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2177558 (2.1 MB)  TX bytes:458513 (458.5 KB)


lspci -nn | grep 0280
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

sudo iwlist wlan0 freq

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: B0:A7:37:13:52:13
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-559-03DB9C"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a3ad55bf
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00164449524543542D726F6B752D3535392D303344423943
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ABC1916FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD090010180200004C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DDAE0050F204104A0001101044000102103B0001031047001022210203040506070809B0A73713521310210004526F6B7510230014526F6B752053747265616D696E6720537469636B1024001833353030582076657220352E36206275696C6420323034371042000C324C2A2A2A2A2A2A2A3535391054000800060050F2040001101100164449524543542D726F6B752D3535392D303344423943100800020000103C0001011049000600372A000120
                    IE: Unknown: DD16506F9A0A00000600111C4400960A0006B2A737135211
          Cell 02 - Address: 00:00:00:00:00:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"JRLeimer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000052996f15d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00084A524C65696D6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010F239EB3CA7EC51ED502FA429356E0780102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180205001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:1E:2A:69:46:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption keyon
                    ESSID:"RIGIDCHOPPER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d595c6b82
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C524947494443484F50504552
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F0201010F0002A44000
                    IE: Unknown: DD1A00037F0301000000001E2A69465E021E2A69465E64002C011D08
          Cell 04 - Address: 90:48:9A:5A:30:EC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption keyon
                    ESSID:"DVW3201B7F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001463389083c
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A44565733323031423746
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010161BBE5F831A66E2D6BB5CCCE5CBF079102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203000C0000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 05 - Address: 14:2D:27:6F:02:3E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption keyon
                    ESSID:"JRLeimer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000528d1b19e
                    Extra: Last beacon: 13792ms ago
                    IE: Unknown: 00084A524C65696D6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180205001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



sorry for the long post..but want to get this problem figured out.

---

### Post by chili555 on 2014-12-11
> i went to the asus wifi disabled (hard-blocked) post and followed the directions as what to do to fix the problem. this time it didnt even work.Once again, your wireless is not hard- or any other blocked. That is a separate and unrelated problem from "wireless tries and fails to connect."

With the USB detached, try to connect and then run:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20 >  wifi.txt
```Connect the USB, connect to the forum and copy and paste the file wifi.txt in your reply.

---

### Post by NyteRukh on 2014-12-11
here's the result:

Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Activation (wlan0/wireless): connection 'JRLeimer 1' has security, and secrets exist.  No new secrets needed.
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Config: added 'ssid' value 'JRLeimer'
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Config: added 'scan_ssid' value '1'
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Config: added 'auth_alg' value 'OPEN'
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Config: added 'psk' value '<omitted>'
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> Config: set interface ap_scan to 1
Dec 11 18:30:08 BibBoy NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec 11 18:30:09 BibBoy NetworkManager[757]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 11 18:30:09 BibBoy NetworkManager[757]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Dec 11 18:30:09 BibBoy NetworkManager[757]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 11 18:30:33 BibBoy NetworkManager[757]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> NetworkManager state is now DISCONNECTED
Dec 11 18:30:33 BibBoy NetworkManager[757]: <warn> Activation (wlan0) failed for connection 'JRLeimer 1'
Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 11 18:30:33 BibBoy NetworkManager[757]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

---

### Post by chili555 on 2014-12-11
> Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> NetworkManager state is now DISCONNECTED
Dec 11 18:30:33 BibBoy NetworkManager[757]: <warn> Activation (wlan0) failed for connection '[COLOR="#FF0000"]JRLeimer 1[/COLOR]'However, scanning says the network is named:> Cell 05 - Address: 14:2D:27:6F:02:3E
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=46/70 Signal level=-64 dBm 
Encryption keyn
ESSID:"[COLOR="#FF0000"]JRLeimer[/COLOR]"That is, without the 1 at the end. I suggest you delete JRLeimer 1 from Network Manager and try again.

---

### Post by NyteRukh on 2014-12-11
JRLeimer is the wifi usb stick
JRLeimer1 is the onboard wifi

---

### Post by chili555 on 2014-12-11
I don't believe either has an SSID name.Only access points, typically in home and small office settings, routers, have a name, also known as SSID. Your router's SSID is:> Cell 05 - Address: 14:2D:27:6F:02:3E
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=44/70 Signal level=-66 dBm 
Encryption keyon
ESSID:"[COLOR="#FF0000"]JRLeimer[/COLOR]"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000528d1b19e
Extra: Last beacon: 13792ms agoNetwork manager has a profile stored and it evidently believes it is to connect, by default, to:> Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Dec 11 18:30:33 BibBoy NetworkManager[757]: <info> NetworkManager state is now DISCONNECTED
Dec 11 18:30:33 BibBoy NetworkManager[757]: <warn> [COLOR="#FF0000"]Activation (wlan0) failed for connection 'JRLeimer 1'[/COLOR]I don't really know how else to explain 'SSID not found.'

---

### Post by NyteRukh on 2014-12-11
yes but in the network manager it shows two connections with the name JRLeimer. since i have two wifi devices attached to the laptop Ubuntu has named them JRLeimer and JRLeimer1



when i disconnect the usb stick..the onboard wifi adapter becomes JRLeimer and unable to connect even tho it tries..when i use the usb stick, it becomes JRLeimer, if i explained it correctly

---

### Post by NyteRukh on 2015-03-08
i have figured out the problem with the wirelesss.. when i was first attempting to use the wireless, i was using a cable modem/wifi router combo that was installed when time warner hooked up my internet. i recently bought my own cable modem/wireless router and the wireless works great now. thanks to all who have tried to help me.

---

