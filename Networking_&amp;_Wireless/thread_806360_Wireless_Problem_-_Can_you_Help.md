---
title: "Wireless Problem - Can you Help ?"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by kbow on 2008-05-24
Hi -

I think I am getting so close with my wireless, but it seems to be connecting and disconnecting from my WRT54G. Even when it seems connected, I am not able to ping the gateway at 192.168.1.1 so it seems still like a wireless issue.

Here is the wireless hardware etc ...

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)kj

Here is the output from dmesg -

[ 2602.302685] wlan0: authenticate with AP 00:0f:66:02:49:69
[ 2602.303988] wlan0: RX authentication from 00:0f:66:02:49:69 (alg=0 transaction=2 status=0)
[ 2602.303996] wlan0: authenticated
[ 2602.303999] wlan0: associate with AP 00:0f:66:02:49:69
[ 2602.306403] wlan0: RX ReassocResp from 00:0f:66:02:49:69 (capab=0x431 status=0 aid=1)
[ 2602.306408] wlan0: associated
[ 2602.306413] wlan0: switched to short barker preamble (BSSID=00:0f:66:02:49:69)
[ 2606.242665] wlan0: RX deauthentication from 00:0f:66:02:49:69 (reason=15)
[ 2606.242672] wlan0: deauthenticated
[ 2607.240444] wlan0: authenticate with AP 00:0f:66:02:49:69
[ 2607.241586] wlan0: RX authentication from 00:0f:66:02:49:69 (alg=0 transaction=2 status=0)
[ 2607.241593] wlan0: authenticated
[ 2607.241597] wlan0: associate with AP 00:0f:66:02:49:69
[ 2607.243351] wlan0: RX ReassocResp from 00:0f:66:02:49:69 (capab=0x431 status=0 aid=1)
[ 2607.243358] wlan0: associated
[ 2607.243363] wlan0: switched to short barker preamble (BSSID=00:0f:66:02:49:69)
***********************************************************************
Here is the output from iwlist scanning

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:02:49:69
                    ESSID:"aircom"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/100  Signal level=-62 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000011163c4f7ce

Here is the output from iwconfig (Notice Bit Rate only 1 Mb/s)


wlan0     IEEE 802.11g  ESSID:"aircom"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:02:49:69   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=109/100  Signal level=-45 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
*********************************************************************



*********************************************************************
Attempting to connect to a Linksys WRT54G ver 2
*********************************************************************

Here is the output from route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0



Does anyone have an idea of what's going on here. FYI - Same system booted into XP connects fine,


Thanks Let me know anymore info you may need.

Thanks

---

### Post by kbow on 2008-05-25
Any ideas ?

Sorry for the selfish bump .....

---

### Post by prshah on 2008-05-25
> **kbow said:**
> 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)kj


Are you using the broadcom native driver or windows driver thru ndiswrapper?

---

### Post by kbow on 2008-05-25
Thanks -

Here are the results of lshw -C network

product: BCM4312 802.11a/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 32 bits
clock: 33 Mhz
capabilites: bus_master cap_list
**configuration: driver=b43-pci-bridge latency=0 module=ssb**

I did not use NDIS wrapper, I used the fwcutter.

Thanks

---

### Post by kbow on 2008-05-25
Just a bit more info, since it may be helpful to others. First of all, I am connecting to my wireless network now finally, and getting out to the Internet although I am still having some issues.

I am in Roaming mode, and I am using the WPA_SUPPLICANT.CONF

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="air"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="TEST"
        pairwise=TKIP
        group=TKIP
}


Initally, I was having better than 50 % packet loss with what seemed to be the wireless being up and down, but later I realized that I may have some routing issues going on, and running ifconfig eth0 down dropped my packet loss to 1 to 3 %.

Current Routing Table with eth0 down

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0


With the eth0 up I have horrible performance, and even pinging the gateway produces high ping times, since it's trying to use the eth0 connection.

I can provide more details, if someone would like to work this issue as possibly a bug, since it's interesting that what seemed like poor wireless performance with the b43 may just be a route issue that only exists with the eth0 interface up. I have not totally figured this out yet, but you can see my current routing table above and you can look earlier in my post to what it is with the eth0 up.

Thanks

---

### Post by kbow on 2008-05-26
Can you have multiple networks in the wpa_supplicant.conf file ? Will the laptop auto-detect the new network ?

---

