---
title: "Dual boot Machine dropping connection only on Ubuntu. DHCP?"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by Mike1977 on 2013-10-11
Here are the facts:
Despite that my computer is literally 5 feet away from my router, I get periodic disconnects. Also, most of the time my wifi icon reads 3 out of 4 bars. I run a 3rd party VPN, and although the disconnect is for only a second, I lose my vpn connection. This causes me to have to monitor my icon to make sure there was no drop. I'll mention now that I also lose connection while on clean , non VPN connection. I watch the wifi icon constantly fluctuating.
Before I go any further I'll mention that I am on a Toshiba Satellite L755. I am running dual boot Operating systems, Windows 7 and Ubuntu 12.04 LTS. I have already sent a log to my VPN server who shows that there are no errors on their end. Plus, I'm not always connected through vpn, yet I still get a popup saying "disconnected". Also, I have no issue with droped connections while running Windows7 on this machine.
So for the past week, I have been trying everything and anything that comes up in my search. It's worth saying that I am doing these things blindly, and have no idea if they actually pertain to my issue, but since it was suggested to other users with similar problems, I tried it.  Here's what I've tried so far that has not worked:
 When I command    `sudo lspci` it shows that my network controller is


    Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)


It was suggested somewhere that I try    `sudo iwconfig wlan0 power off` 
To which I get this:


"Error for wireless request "Set Power Management" (8B2C) : SET failed on device wlan0 ; Operation not supported". Whether this has anything to do with my problem, I have no idea.


It was suggested I go into "System Settings>Additional Drivers and I found :


 "No proprietary drivers are in use on this system"


I found alot of common answers were based on the fact that my driver , Realtek , does not play well or work with Ubuntu. It was suggested on similar threads to download a new driver. Here are the steps I followed.    
`sudo apt-get install gcc build-essential linux-headers-generic linux-headers-$(uname -r)`
for necessary dependencies


1) Download driver from :realtek website    
`http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722` 
and copy it to your desktop (it's about 12 MB download).


2) Right-click the downloaded file (linux_mac80211_0012.0207.2013.tar.bz2) > "Extract here". This will extract a folder named "rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_001 2.0207.2013" on your desktop.


3) Open a terminal (Ctrl+Alt+T) and run following commands :
Code:


    cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
    make
    sudo make install


4) Reboot or manually load the driver with -
Code:


    sudo modprobe -v rtl8188ee


After doing this, nothing changed. I restarted the computer, and still had the same issues.
I mention that after doing step 3 above, I get a long scroll of activity, but there a number of error messages: ![error after install][2]


It is at this point that I get help to my question, and was told to try this:


""""First, let's clean up the file from your first attempt:


    cd Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
    make clean


Now, let's modify one file:


    gedit pci.h


At the top of the file,after the comment section all out lined in **, add this sequence:


    #ifndef __devinit
    #define __devinit
    #define __devinitdata
    #endif




Proofread carefully, save and close gedit. Now do:


    make
    sudo make install


Finally, I believe the driver you need is rtl8192ce and not rtl8188ee:


    sudo modprobe rtl8192ce


Your wireless should now be working"""".






AT first, I noticed that I had 4 bars in wifi(instead of 3) Apparently there is no other way to see if what I did actually worked though. It wasn't until yesterday that I noticed that the disconnection problem still persisted. So far while typing this question, my signal has dropped twice. At this point, I've tried everything in all the threads that I could find. I don't know where to go next. ANY HELP?


Here, I confirm driver by entering:
    
    lsmod | grep rtl


My Results:


    rtl8192ce             141806  0 
    rtlwifi               123323  1 rtl8192ce
    mac80211              630977  2 rtl8192ce,rtlwifi
    cfg80211              525326  2 rtlwifi,mac80211

ALSO, Whether or not my Power Management is ON or OFF by running:


    iwconfig | grep Power


My Results:


    tun0      no wireless extensions.
    
    eth0      no wireless extensions.
    
    lo        no wireless extensions.
    
              Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
              Power Management:off


ALSO I took the liberty of running:


    lspci -nn | grep 0280


My Results:


    02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)


FURTHER EDITS: Within 5 minutes after disconnect I run this:


    ~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20


MY RESULTS:


 


    Oct  9 18:49:57 Mike-Ubuntu12 kernel: [ 6452.055962] wlan0: RX AssocResp from 58:6d:8f:89:14:46 (capab=0x11 status=0 aid=3)
    Oct  9 18:49:57 Mike-Ubuntu12 kernel: [ 6452.056232] wlan0: associated
    Oct  9 18:49:57 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: authenticating -> associated
    Oct  9 18:49:57 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
    Oct  9 18:49:57 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
    Oct  9 18:51:42 Mike-Ubuntu12 kernel: [ 6557.222852] wlan0: Connection to AP 58:6d:8f:89:14:46 lost
    Oct  9 18:51:42 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: completed -> disconnected
    Oct  9 18:51:42 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): roamed from BSSID 58:6D:8F:89:14:46 (HighMoon) to (none) ((none))
    Oct  9 18:51:42 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: disconnected -> scanning
    Oct  9 18:51:43 Mike-Ubuntu12 kernel: [ 6558.171237] wlan0: authenticate with 58:6d:8f:89:14:46
    Oct  9 18:51:43 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: scanning -> authenticating
    Oct  9 18:51:43 Mike-Ubuntu12 kernel: [ 6558.190989] wlan0: send auth to 58:6d:8f:89:14:46 (try 1/3)
    Oct  9 18:51:43 Mike-Ubuntu12 kernel: [ 6558.192747] wlan0: authenticated
    Oct  9 18:51:43 Mike-Ubuntu12 kernel: [ 6558.194187] wlan0: associate with 58:6d:8f:89:14:46 (try 1/3)
    Oct  9 18:51:43 Mike-Ubuntu12 kernel: [ 6558.197471] wlan0: RX AssocResp from 58:6d:8f:89:14:46 (capab=0x11 status=0 aid=3)
    Oct  9 18:51:43 Mike-Ubuntu12 kernel: [ 6558.197782] wlan0: associated
    Oct  9 18:51:43 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: authenticating -> associated
    Oct  9 18:51:43 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
    Oct  9 18:51:43 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
    Oct  9 18:51:48 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): roamed from BSSID (none) ((none)) to 58:6D:8F:89:14:46 (HighMoon)






I tried $ `iwconfig wlan0`  WHILE I WAS ON NORMAL /NON VPN CONNECTION. My Results:




    wlan0     IEEE 802.11bgn  ESSID:"HighMoon"  
              Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:89:14:46   
              Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
              Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
              Power Management:off
              Link Quality=70/70  Signal level=-22 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:11   Missed beacon:


 WHILE RUNNING CLEAN/NO VPN , MY COMPUTER DISCONNECTED. Here is the readout directly after the disconnect.


I Run:    `~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20`


    interface wlan0.IPv4 with address 192.168.1.116.
    Oct 10 18:19:08 Mike-Ubuntu12 avahi-daemon[959]: New relevant interface wlan0.IPv4 for mDNS.
    Oct 10 18:19:08 Mike-Ubuntu12 avahi-daemon[959]: Registering new address record for 192.168.1.116 on wlan0.IPv4.
    Oct 10 18:19:08 Mike-Ubuntu12 dhclient: XMT: Info-Request on wlan0, interval 930ms.
    Oct 10 18:19:09 Mike-Ubuntu12 NetworkManager[970]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
    Oct 10 18:19:09 Mike-Ubuntu12 NetworkManager[970]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
    Oct 10 18:19:09 Mike-Ubuntu12 NetworkManager[970]: <info> Policy set 'HighMoon' (wlan0) as default for IPv4 routing and DNS.
    Oct 10 18:19:09 Mike-Ubuntu12 NetworkManager[970]: <info> Activation (wlan0) successful, device activated.
    Oct 10 18:19:09 Mike-Ubuntu12 NetworkManager[970]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
    Oct 10 18:19:09 Mike-Ubuntu12 dhclient: XMT: Info-Request on wlan0, interval 1800ms.
    Oct 10 18:19:11 Mike-Ubuntu12 dhclient: XMT: Info-Request on wlan0, interval 3510ms.
    Oct 10 18:19:15 Mike-Ubuntu12 dhclient: XMT: Info-Request on wlan0, interval 7250ms.
    mike@

Can anyone help me?
Here is the original thread on AskUbuntu : [http://askubuntu.com/questions/355581/one-week-in-and-still-having-disconnect-issues-tried-everything-i-could-find-o](http://askubuntu.com/questions/355581/one-week-in-and-still-having-disconnect-issues-tried-everything-i-could-find-o)

---

### Post by varunendra on 2013-10-12
First off, Welcome to the forums Mike !:)

I see you were already being assisted by the best person here, chili555. Looks like you added this info 'After' his last comment on you askubuntu post (because he can't miss it) -
> **Mike1977 said:**
>     Oct  9 18:49:57 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
    Oct  9 18:51:42 Mike-Ubuntu12 kernel: [ 6557.222852] wlan0: Connection to AP 58:6d:8f:89:14:46 lost
    Oct  9 18:51:42 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: completed -> disconnected
    Oct  9 18:51:42 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): [COLOR="#FF0000"]**roamed** from BSSID 58:6D:8F:89:14:46 (HighMoon) to (none) ((none))[/COLOR]
....
....
    Oct  9 18:51:43 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
    Oct  9 18:51:48 Mike-Ubuntu12 NetworkManager[975]: <info> (wlan0): [COLOR="#FF0000"]**roamed** from BSSID (none) ((none)) to 58:6D:8F:89:14:46 (HighMoon)[/COLOR]

Accordingly, I'd suggest to save your access-point's MAC address (58:6D:8F:89:14:46) in the "BSSID" field in the connection settings in Network Manager, like the screenshot below -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246894[/IMG]

Save and close the settings and retry to connect. If it still drops out, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

**PS:**
Oh, and you should use 'Code' tags to post the output parts. It preserves its formatting and makes the post compact and more readable :)
Please follow the "Using Code Tags" link in my signature below to see how to use it.

---

### Post by Laurence02 on 2013-10-13
Wow.. No I know this for my new install!. That was so irritating!

---

### Post by Mike1977 on 2013-10-13
Thanks Varunendra. I had a feeling I was typing in wrong format.I  apologize for that long, run on question :) Anyways, I'm having a  problem opening the Network Manager, to enter the BSSID. I'm typing  > nm-connection-editor in Terminal, but I'm not getting any  option to edit anything. What am I doing wrong? Thanks

---

### Post by varunendra on 2013-10-13
> **Mike1977 said:**
> ..I'm having a  problem opening the Network Manager, to enter the BSSID. I'm typing   in Terminal..

Not in terminal, it has to be entered in the GUI of Network Manager. If you are using default version of Ubuntu, look at the top right corner for this icon -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246912[/IMG]

Click on it to produce the drop-down menu > click "Edit Connections" > goto "Wireless" tab > double-click your connection to edit it > locate the BSSID field under "Wireless" tab > Enter your Access-Point's MAC address in the "BSSID" field > Save > Close and done !

If you are using a different desktop environment than Unity, find the option to edit the network connections from menu, tray or wherever it is located.

Try it, and let us all know if it works as expected for you too. :)

---

### Post by Mike1977 on 2013-10-14
Thanks Varunendra,
I have not been on Ubuntu too much this past weekend, but I have changed the BBSID number in the field ( the field was blank before). I just connected today today, and although I have not had any disconnects in the past 20 minutes, I am already seeing that the wifi icon is fluctuating. Sometimes to no bars(yet staying connected, apparently) Should I wait until it disconnects before I run the "wireless script" in your signature? Or is there another step to try? Thanks.
EDIT: 5 MINUTES LATER AND IT DISCONNECTED. I'll post the results below.

---

### Post by Mike1977 on 2013-10-14
```
#
*************** info trace ***************

***** uname -a *****

Linux Mike-Ubuntu12 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fc50]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b289 Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"HighMoon"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192ce             141806  0 
rtlwifi               123323  1 rtl8192ce
mac80211              630977  2 rtl8192ce,rtlwifi
cfg80211              525326  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [HighMoon] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           7 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    mccoy:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Kenny:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    HighMoon-guest:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    *HighMoon:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    NETGEAR50:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75
    DNS:             192.168.1.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"HighMoon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0008486967684D6F6F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001002519461683B1AF5B2843176671BB6DB102100074C696E6B7379731023000D4C696E6B7379732045343230301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"HighMoon-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000E486967684D6F6F6E2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"mccoy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015ec45a872
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00056D63636F79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR50"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028a43ae501c
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00094E4554474541523530
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010620A080DB957EB4BE3B0A59CD15F81E21021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Kenny"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002eb5931180
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 00054B656E6E79
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B


***** resolv.conf *****

nameserver 127.0.0.1
search hsd1.pa.comcast.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8371CA3A9E899B11125FFDE
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C5BE23342E67ABA5ADA703E
depends:        mac80211,cfg80211
vermagic:       3.8.0-31-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   10.371170] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.371388] rtlwifi: wireless switch is on
[   18.839026] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.841035] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.155469] wlan0: authenticate with <MAC address removed>
[   23.175505] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.177173] wlan0: authenticated
[   23.178972] wlan0: associate with <MAC address removed> (try 1/3)
[   23.182057] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[   23.182291] wlan0: associated
[   23.182298] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1169.464837] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1173.401798] wlan0: authenticate with <MAC address removed>
[ 1173.420409] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1173.422026] wlan0: authenticated
```

---

### Post by varunendra on 2013-10-14
> **Mike1977 said:**
> ```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: **[COLOR="#0000CD"]rtl8192ce[/COLOR]**
....
    *HighMoon:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
....
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
           ....
                    ESSID:"HighMoon"
                    ....
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
```
First and foremost, please change the encryption type in the router from WPA/WPA2 mixed mode to pure WPA2-PSK (AES/CCMP) only. No mixed mode, no TKIP. Please refer to your router's user manual to see how to do that. Change it and reboot the router to make sure the new settings are effective.

Then in Ubuntu, please try a few parameters with your driver as suggested in [post=12815912]this post[/post].

Like mentioned in the above linked post, those parameters will be temporary and will be lost at next boot. If any of them could help stability, we'll make it permanent.

To make them permanent, use the method in [post=12815984]this post[/post] (ignore the initial part, read from *"For example, to make the "swenc=1" option permanent....."*).

Please post back the progress and we can try other things if necessary.

---

### Post by Mike1977 on 2013-10-15
Could you give me a little clarification as to why I should change the settings in wireless security from "mixed mode" to Wpa2? From my reading, I see that my settings as they are now, are the most secure, and I don't have any connection issues while running Windows 7 on this laptop. So, I'm wondering, do I have have to make my wireless security more vulnerable just to be able to use Ubuntu? It is saying in many of the Cisco forums that Mixed mode is what I want.  OR are you saying I have to change to a different setting in order to be able to run the parameters you provided?
Also. I have two bands to change from mix mode. 5GHZ and 2.4GHZ. 
And the choices to select are:
WPA2 personal, WPA Personal, WPA2/WPA enterprise mixed mode, WPA2 enterprise, WPA enterprise, wep, radius, and disable. My router is a Linksys E4200.
Thanks Varunendra

---

### Post by varunendra on 2013-10-15
> **Mike1977 said:**
> Could you give me a little clarification as to why I should change the settings in wireless security from "mixed mode" to Wpa2? From my reading, I see that my settings as they are now, are the most secure, and I don't have any connection issues while running Windows 7 on this laptop. So, I'm wondering, do I have have to make my wireless security more vulnerable just to be able to use Ubuntu? It is saying in many of the Cisco forums that Mixed mode is what I want.
I'm glad you brought it up. **If** you are concerned about enhanced security, then **No**, the mixed mode you are currently using is certainly **NOT** what you want. I'll very happily share the details why -

The most advanced and most secure encryption protocol is WPA2, and the most secure (and probably the most efficient too at the same time) encryption algorithm is AES which is the base of CCMP.

The most outdated and most insecure encryption protocol (for wifi) is WEP, and WPA (not WPA2) is not much different from it and uses the weak and very inefficient encryption algorithm TKIP. TKIP is not only weak, but is inefficient too, thus severely limiting the throughput on the device (you can't go above 54 Mb/s with TKIP).

So the WPA/WPA2 mixed mode is used for backward compatibility purpose and the WPA-TKIP part of it is the vulnerable part. The only reason why one should use the mixed mode is if they have one of those ancient hardware which can't support the modern WPA2 (AES) encryption. Otherwise, just get rid of it.

Some facts about these -

WPA & WPA2 ([http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)) -
> WPA (sometimes referred to as the draft IEEE 802.11i standard) became available in 2003. **The Wi-Fi Alliance intended it as an intermediate measure in anticipation of the availability of the more secure and complex WPA2.**
....
WPA uses a message integrity check algorithm called Michael to verify the integrity of the packets. Michael is much stronger than a CRC, but **not as strong as the algorithm used in WPA2**.
....
**WPA2 has replaced WPA**. WPA2,.... In particular, **it introduces CCMP, a new AES-based encryption mode with strong security.**


TKIP Vs AES or CCMP ([http://en.wikipedia.org/wiki/CCMP#Security](http://en.wikipedia.org/wiki/CCMP#Security)) -
> CCMP is the standard encryption protocol for use with the WPA2 standard and **is much more secure than the WEP protocol and TKIP protocol of WPA**.

So clearly, it is the mixed mode that is not only inefficient, but is also more vulnerable compared to pure WPA2-PSK with AES.

Now why windows 7 works nicely with it is obvious. All the hardware manufacturers keep windows as a standard while designing their hardware, and the same is true for the drivers they provide. Thus both the hardware and the driver are 'optimized' for windows and can take care of the added complexity caused by such inefficient combinations. Note here that the added 'complexity' is not adding any security here, on the contrary, is compromising it.

Almost no hardware is specifically designed for Linux and most of the drivers are developed by the open source community, either by the "partially" disclosed information by the manufacturer, or reverse-engineering. Hence they are obviously not as efficient as the drivers designed by the manufacturers themselves and constantly being upgraded by them.

But the capability of Open Source shines when it comes to stuff closer to real universal 'Standards' (not 'patches' to match a particular OS). Hence the Linux drivers can handle the WPA2-AES encryption much better than the mixed mode. Windows drivers should be able to handle all the available modes just fine, so you shouldn't notice any negative effect after changing the encryption. If anything, it will only be enhanced (due to getting rid of TKIP).

> OR are you saying I have to change to a different setting in order to be able to run the parameters you provided?
The parameters I provided would work in any case, only they will work much better when the encryption type is optimized too. Please note that none of the parameters is 'guaranteed' to enhance the speed or connectivity, but most often they do.

> Also. I have two bands to change from mix mode. 5GHZ and 2.4GHZ. 
And the choices to select are:
WPA2 personal, WPA Personal, WPA2/WPA enterprise mixed mode, WPA2 enterprise, WPA enterprise, wep, radius, and disable. My router is a Linksys E4200.
The 5GHz band is still not well supported by many Linux drivers. I'm not sure if rtl8192ce can support it or not. So it is safer to disable the 5GHz mode, if none of the devices on your network are getting advantage of the extra speeds offered by it (300 Mb/s +). Either use 2.4 GHz only, or mixed mode.

For encryption, WPA2 personal is what you want, with AES or CCMP being the encryption algorithm (or 'Ciphers').

Hope it clears your doubts, and helps making the connection better. :)

---

### Post by Mike1977 on 2013-10-15
Ok great.  I appreciate this.  I'll dig into it tomorrow,  and change the settings on the router.  Can I ask,  is AES CCMP algorythm implied with WPA2, or is that something I would have to find and change as well? I'm asking because the cisco forums were also saying that TKIP was no longer a separate setting,  or a selection to change,  but included with WPA/WPA2 mix mode. So I'm wondering if that's also the case with WPA2 personal and Aes/CCMP currently.  I mean,  if i change my wireless setting in router to WPA2 personal, will that automatically delete TKIP, allowing replacement by AES/CCMP? Thanks,  this was a good read,  and the Windows patch makes sense to me.

---

### Post by varunendra on 2013-10-15
> **Mike1977 said:**
> is AES CCMP algorythm implied with WPA2, or is that something I would have to find and change as well? I'm asking because the cisco forums were also saying that TKIP was no longer a separate setting,  or a selection to change,  but included with WPA/WPA2 mix mode. So I'm wondering if that's also the case with WPA2 personal and Aes/CCMP currently.  I mean,  if i change my wireless setting in router to WPA2 personal, will that automatically delete TKIP, allowing replacement by AES/CCMP?
It *should* be implied. But with some wierd settings I have seen in some routers, I have doubts. See this screenshot -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246988[/IMG]

It shows the selected Encryption mode to be WPA-PSK, which I think shouldn't leave the option of anything other than TKIP, both AES and TKIP options are available. To me, it means that either that model does not provide the option of WPA2 exclusively (might be selected implicitely if you selected "AES"), or it may use some weird non-standard setting.

As such, check the options available to you in 'Your' router, and make sure to choose the correct one explicitly if possible.

---

### Post by Mike1977 on 2013-10-18
Hi Varun, 
So I'm having an issue here.  I changed the settings on 2.4ghz to wpa2, and disabled 5ghz. I clicked "save settings" and the popup window went away. I tried to then enter my router settings again,  to restart,  but it would not connect to Internet.  It Now gives me "Install Cisco connect to setup router" I already have Cisco connect in programs,  but I went through the steps anyways. .. That Did not work.  I also unplugged router and restarted, and that did not work.  While trying to enter settings advanced , it says "class not registered"
EDIT: I pushed forward on network,  and entered my ip in browser,  and was able to access the settings again.  I changed 5ghz from disabled to wpa2 personal. Then I went back to main settings page and clicked reboot. Seems to be connecting fine now. Properties list wpa2 personal/ aes

---

### Post by Mike1977 on 2013-10-18
Ok, 
So I moved forward with the first link you posted above, with the parameters to try. Just to be clear: I have both 5ghz and 2.4GHZ set to WPA2-personal with AES encryption. 
The first command in your link totally disconnected my computer. So I tried the second command, and it is now re-connected. However, I am still showing 3 out of 4 bars on wifi icon, and it's fluctuating. Here is the readout from the first two commands in terminal:
> # sudo modprobe -rv rtl8192ce
[sudo] password for mike: 
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko
mike@Mike-Ubuntu12:~$ sudo modprobe -rv rtl8192ce
mike@Mike-Ubuntu12:~$ sudo modprobe -v rtl8192ce fwlps=0
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko fwlps=0 #

EDIT: OK so I've done all 4 parameters. I still have 3 out of 4 bars showing, and I am 4 feet away from my router (wireless). I don't know if this really matters here, but I ran speedtest and am getting 10ms PING, 55.92 down and 11.53 up. I am on clean non vpn while trying all these teminal commands. I have a few things to do online here. So , I'll monitor the connection and see if it drops/disconnects like it has been before. Time will tell.

> #mike@Mike-Ubuntu12:~$ sudo modprobe -rv rtl8192ce
[sudo] password for mike: 
Sorry, try again.
[sudo] password for mike: 
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko
mike@Mike-Ubuntu12:~$ sudo modprobe -rv rtl8192ce
mike@Mike-Ubuntu12:~$ sudo modprobe -v rtl8192ce fwlps=0
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko fwlps=0
mike@Mike-Ubuntu12:~$ sudo modprobe -rv rtl8192ce
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko
mike@Mike-Ubuntu12:~$ sudo modprobe -v rtl8192ce ips=0
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko ips=0
mike@Mike-Ubuntu12:~$ sudo modprobe -rv rtl8192ce
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko
mike@Mike-Ubuntu12:~$ sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko swenc=1 ips=0 fwlps=0
mike@Mike-Ubuntu12:~$ #

---

### Post by Mike1977 on 2013-10-18
I ran your wireless script again. I haven't rebooted yet, so I figured I'd run your wireless script before doing so.

```
*********** info trace ***************

***** uname -a *****

Linux Mike-Ubuntu12 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fc50]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b289 Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"HighMoon"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


***** rfkill *****

3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192ce             141806  0 
rtlwifi               123323  1 rtl8192ce
mac80211              630977  2 rtl8192ce,rtlwifi
cfg80211              525326  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HighMoon] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    mccoy:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    HighMoon-guest:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94
    *HighMoon:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 88 WPA2

  IPv4 Settings:
    Address:         192.168.1.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75
    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"HighMoon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0008486967684D6F6F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001002519461683B1AF5B2843176671BB6DB102100074C696E6B7379731023000D4C696E6B7379732045343230301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Kenny"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e0bbbf826
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 00054B656E6E79
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"HighMoon-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000E486967684D6F6F6E2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"mccoy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cc490c33e
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00056D63636F79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180206F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1
search hsd1.pa.comcast.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8371CA3A9E899B11125FFDE
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C5BE23342E67ABA5ADA703E
depends:        mac80211,cfg80211
vermagic:       3.8.0-31-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   10.515839] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.516029] rtlwifi: wireless switch is on
[   19.204605] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.206176] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.639618] wlan0: authenticate with <MAC address removed>
[   24.659702] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.661341] wlan0: authenticated
[   24.663164] wlan0: associate with <MAC address removed> (try 1/3)
[   24.666506] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[   24.666726] wlan0: associated
[   24.666735] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  165.223326] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[  166.524363] wlan0: authenticate with <MAC address removed>
[  166.543916] wlan0: send auth to <MAC address removed> (try 1/3)
[  166.545589] wlan0: authenticated
[  166.547099] wlan0: associate with <MAC address removed> (try 1/3)
[  166.553047] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[  166.553322] wlan0: associated
[  758.271726] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  758.271808] wlan0: Connection to AP <MAC address removed> lost
[  758.277756] rtlwifi-0:rtl_action_proc():<10000-1> sta is NULL
[  759.220040] wlan0: authenticate with <MAC address removed>
[  759.239395] wlan0: send auth to <MAC address removed> (try 1/3)
[  759.242098] wlan0: authenticated
[  759.242604] wlan0: associate with <MAC address removed> (try 1/3)
[  759.246178] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[  759.246434] wlan0: associated
[  796.614627] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  869.875685] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  869.875994] rtlwifi: wireless switch is on
[  870.236469] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  870.240839] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  872.844584] wlan0: authenticate with <MAC address removed>
[  872.864338] wlan0: send auth to <MAC address removed> (try 1/3)
[  872.866869] wlan0: authenticated
[  872.867457] wlan0: associate with <MAC address removed> (try 1/3)
[  872.870819] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[  872.870996] wlan0: associated
[  872.871019] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1402.149103] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1418.649815] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1418.650207] rtlwifi: wireless switch is on
[ 1419.011980] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1419.016519] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1421.623361] wlan0: authenticate with <MAC address removed>
[ 1421.643842] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1421.645907] wlan0: authenticated
[ 1421.646956] wlan0: associate with <MAC address removed> (try 1/3)
[ 1421.650521] wlan0: RX AssocResp from <MAC address removed> (capab=0x11 status=0 aid=2)
[ 1421.650821] wlan0: associated
[ 1421.650846] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1490.957592] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1494.670146] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1494.670883] rtlwifi: wireless switch is on
[ 1495.026842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1495.031110] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1497.666236] wlan0: authenticate with <MAC address removed>
[ 1497.686126] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1497.688380] wlan0: authenticated
[ 1497.689441] wlan0: associate with <MAC address removed> (try 1/3)
[ 1497.692869] wlan0: RX AssocResp from <MAC address removed>
```

---

### Post by varunendra on 2013-10-18
Everything looks pretty solid to me, including the speeds you mentioned. You should probably try changing the channel from 11 to 1, as both the other APs are using the same channel/frequency, could be causing some interference.

Let's take a look at the current parameters in use. Please post back the output of -
```
grep -R [[:alnum:]] /sys/module/rtl8192ce/parameters
```

If (and only if, since the speeds are fine now) the stability gives too much trouble, also try disabling the N-channel in the router (use b/g-only mode). Although, as you may have guessed, it is a compromise with speeds your router can deliver, but just test it (again, only if stability is still poor) and then decide whether you want to keep it that way or not.

**EDIT:**
Oh, and by "looking at current parameters" I mean to see which ones you have applied and whether they were applied correctly or not. Of course if you haven't made them permanent yet they will revert to defaults at next boot, unless you apply them again.

I suggest you make them permanent anyway and then test/post back. It is as easy to revert as deleting the .conf file -
```
sudo rm /etc/modprobe.d/rtl8192ce.conf
```

---

### Post by Mike1977 on 2013-10-19
I had already re booted after seeing your post. So I figured, before establishing the parameters again, I would run the code you provided. Just to see what it read out as vanilla. Here's the output:

```
/sys/module/rtl8192ce/parameters/ips:Y
/sys/module/rtl8192ce/parameters/fwlps:Y
/sys/module/rtl8192ce/parameters/swenc:N
/sys/module/rtl8192ce/parameters/swlps:N
```

I will now re establish the parameters, and edit this reply with the readout included. But just in case, I will not make the parameters permanent until you see all the readouts and approve.

EDIT 1 : As I said before, the first code command disconnects my wifi fully
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```
. 
So I ran the 2nd code/ parameter you provided:
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce fwlps=0
```

```
/sys/module/rtl8192ce/parameters/ips:Y
/sys/module/rtl8192ce/parameters/fwlps:N
/sys/module/rtl8192ce/parameters/swenc:N
/sys/module/rtl8192ce/parameters/swlps:N
```

Oddly, this time the 3rd parameter had disconnected me too.
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce ips=0
```

 So I ran 4th parameter (blind shot all 3)
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```
 and here is my results:

```
/sys/module/rtl8192ce/parameters/ips:N
/sys/module/rtl8192ce/parameters/fwlps:N
/sys/module/rtl8192ce/parameters/swenc:Y
/sys/module/rtl8192ce/parameters/swlps:N
```

I'm a little confused though. I was guessing that by running the 4th parameter, my results would have been a combination of all 3 readouts. Meaning the top 3 lines would all have "Y" at the end. So which, if any, should I make permanent?  Thanks.

I have not figured out how to change the channel from 11 to 1 yet.

---

### Post by varunendra on 2013-10-19
> **Mike1977 said:**
> I'm a little confused though. I was guessing that by running the 4th parameter, my results would have been a combination of all 3 readouts. Meaning the top 3 lines would all have "Y" at the end. So which, if any, should I make permanent?  Thanks.

Whichever seems to help, which is apparently the fwlps=0 parameter. And none of the 'parameters' should disconnect you, only the first part of each set (modprobe **-r**), due to the "-r" option, which is to 'remove' the driver (thus disabling the interface) so we can reload it with the desired parameter.

And "Y" or "1" means True or Yes, while "N" or "0" means false or No. So the output is in accordance with what you tried.

Based on the response so far, you should try -
```
echo "options rtl8192ce fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
..to make only fwlps=0 parameter permanent.

After doing this, the test command should show you this on next boot -
```
/sys/module/rtl8192ce/parameters/ips:Y
/sys/module/rtl8192ce/parameters/fwlps:N
/sys/module/rtl8192ce/parameters/swenc:N
/sys/module/rtl8192ce/parameters/swlps:N
```

If still disconnecting, you may try the "swenc=1" parameter in temporary mode after this, the fwlps=0 will be loaded automatically. Let me know how it goes. :)

---

### Post by Mike1977 on 2013-10-20
Ok. Seems to be in line with what you thought. I ran the conf* script and rebooted. 

```
mike@Mike-Ubuntu12:~$ grep -R [[:alnum:]] /sys/module/rtl8192ce/parameters
/sys/module/rtl8192ce/parameters/ips:Y
/sys/module/rtl8192ce/parameters/fwlps:N
/sys/module/rtl8192ce/parameters/swenc:N
/sys/module/rtl8192ce/parameters/swlps:N
```

So I guess I just have to see if it disconnects now. I'll let you know. Thanks!

---

