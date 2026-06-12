---
title: "airodump-ng problems, cannot detect networks."
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Scientia on 2008-07-10
I have this linksys wusb54gc that i'm trying to use with airodump-ng.
Now, the first problem i have is the monitor mode problem.

I ran airodump-ng:
> 
johanan@johanan-laptop:~$ sudo airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'
Sysfs injection support was not found either.

So, i disabled the wireless in my computer, and tried airmon-ng start wlan0. This is what i get.

> johanan@johanan-laptop:~$ sudo airmon-ng start wlan0


Interface	Chipset		Driver

wlan0		Ralink 2573 USB	rt73usb - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)

At this stage, iwconfig still lists the mode as managed.

> johanan@johanan-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:AC:DD:1E   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality=32/100  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

Then, i tried with iwconfig instead:
> johanan@johanan-laptop:~$ sudo iwconfig wlan0 mode monitor
johanan@johanan-laptop:~$

iwconfig again, and this time it lists mode as in monitor:
> johanan@johanan-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

So, i figure i can try with airodump again. 
This time, it worked! Or so it seemed..

> CH 3 ][ Elapsed: 1 min ][ 2008-07-10 15:46                                   
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSID
                                                                               
                                                                               
 BSSID              STATION            PWR   Rate  Lost  Packets  Prob

This is how it looked at 1 minute, and the same after 20 minutes.

No networks, no data are found. I know there's something wrong somewhere, but i don't know how to fix this problem.
Please help.

Please note that what i'm doing does not in any way trespass any boundaries, and i'm trying this out on my own wifi network.

---

### Post by Scientia on 2008-07-10
I tried creating a new interface for wlan0 - eth0.

> johanan@johanan-laptop:~$ # iwconfig eth0 create wlandev wlan0 wlanmode monitor

This seemed to work.

Then airmon-ng:
> johanan@johanan-laptop:~$ sudo airmon-ng start eth0
[sudo] password for johanan: 


Interface	Chipset		Driver

wlan0		Ralink 2573 USB	rt73usb - [phy0]

iwconfig:
> 
[QUOTE]johanan@johanan-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

tried airodump with eth0:

> johanan@johanan-laptop:~$ sudo airodump-ng eth0
ioctl(SIOCSIWMODE) failed: Operation not supported

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth0 up; iwconfig eth0 mode Monitor channel <#>'
Sysfs injection support was not found either.

Any help? Anybody?
Could i change the wireless extension from the interface wlan0 to eth0?

Thanks.

---

### Post by Scientia on 2008-07-10
Bump..

Anybody?

---

### Post by Scientia on 2008-07-13
could i somehow change the device from the interface wlan0 to eth0?

---

### Post by bigbugbg on 2008-09-10
same issue here
btw afaik linking wlan-eth wont accomplish anything
either we don't do it right,
or just the drivers+patches are still not right 
for our chipsets

so fat the solutions is ...buying Atheros mini pci card
or wait till they fix it before we do :popcorn:

---

### Post by twisterplus on 2010-02-12
I have the same problem here. Did you find anything on this issue?

---

### Post by twisterplus on 2010-02-12
Actually I found out that I have to listen on mon0 interface instead of wlan1, since it is the monitoring interface.
Have fun

---

### Post by Ansenyi on 2012-01-07
> **twisterplus said:**
> Actually I found out that I have to listen on mon0 interface instead of wlan1, since it is the monitoring interface.
Have fun

Thanks, that helped me out here.

---

