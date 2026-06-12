---
title: "Ad-hoc wireless / hostap setup"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by skadoo on 2007-08-19
I'm having some problems getting an ad-hoc wireless network up. I've done this successfully before (using a Netgear card with the Atheros driver), but I can't make it work with my current setup: an Ambicom 1100C-CF (compact flash) card with hostap.

The card is recognised, and iwconfig reports that it is in ad-hoc mode:

> lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"mrtouchy"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:10:75:1B:9F:BF   
          Bit Rate=11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"mrtouchy"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:10:75:1B:9F:BF   
          Bit Rate=11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-100 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0

iwlist scan reports multiple access points on the local campus network. eg:

> Cell 01 - Address: 00:0B:86:82:D6:70
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level=-55 dBm  Noise level=-73 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10

but not the ad-hoc network (which, btw, is up and running between two other computers in the same room).

My /etc/network/interfaces file is posted below. I'd appreciate any help or suggestions...

> auto lo
iface lo inet loopback

iface wlan0 inet static
        address 192.168.1.91
        netmask 255.255.255.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
        wireless-mode ad-hoc
        wireless-essid mrtouchy
        wireless-key 1234567890 # fake!
        wireless-channel 6
        wireless-rate 11M
auto wlan0


---

### Post by skadoo on 2007-08-19
Oh, just one more thing:

> # /etc/init.d/networking restart
 
* Reconfiguring network interfaces...
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
   ...done.

However this:
> iwconfig wlan0 mode ad-hoc
doesn't report any kind of error.

---

