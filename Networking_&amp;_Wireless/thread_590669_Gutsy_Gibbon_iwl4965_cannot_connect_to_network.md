---
title: "Gutsy Gibbon iwl4965: cannot connect to network"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by marcovanl on 2007-10-25
Hi,

I've just upgraded from 7.04 (Feisty Fawn) to 7.10 (Gutsy Gibbon), hoping that my Intel 4965 AGN would be supported. Unfortunately, I cannot connect to my home network.

The problem seems to be the following (from dmesg:)
> 
[  138.188000] wlan0: Initial auth_alg=0
[  138.188000] wlan0: authenticate with AP 00:0d:72:46:18:a9
[  138.388000] wlan0: authenticate with AP 00:0d:72:46:18:a9
[  138.388000] wlan0: RX authentication from 00:0d:72:46:18:a9 (alg=0 transaction=2 status=0)
[  138.388000] wlan0: authenticated
[  138.388000] wlan0: associate with AP 00:0d:72:46:18:a9
[  138.588000] wlan0: associate with AP 00:0d:72:46:18:a9
[  138.788000] wlan0: associate with AP 00:0d:72:46:18:a9
[  138.988000] wlan0: association with AP 00:0d:72:46:18:a9 timed out

indicating, that somehow, the iwl4965 driver decides to disconnect from the access point.

This might be related to the fact the the wmaster0, which seems to be some kind of control connection, is not working.

For example, if I use the 'manual configuration' and then do 'ifup wlan0', I get a complaint about wmaster0: 
> 
 wmaster0: unknown hardware address type 801

(this comes from dhclient)

In addition, I notice that wmaster0 is not listed when I do iwconfig:
> 
mvl@purple:~$ sudo iwconfig
[sudo] password for mvl:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


On the other hand, wmaster0 is somehow used during the boot sequence
> 
mvl@purple:~$ dmesg | grep wmaster0
[   18.956000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'


Finally, some more info on this card:
> 
mvl@purple:~$ dmesg | grep iwl
[   18.632000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   18.632000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   18.632000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   18.956000] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels


My laptop is a Dell D430.

Any help is appreciated. Please let me know if you need more details.

For the time being, I resort to using ndiswrapper, which seems to work (the default version in Gutsy Gibbon is 1.45, so newer than the one indicated here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty) ). Unfortunately, the connection is not very stable with ndiswrapper.

---

### Post by dbrossard on 2008-02-01
I can confirm this. I think this should be a bug report. Additionally if I try to connect to a network using WPA2 Personal, the authentication works fine but it still cannot associate and times out. I am going to try the driver directly from intel: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

edit:
This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/151627](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/151627)
There are newer drivers you can get. Why doesn't Ubuntu update Gutsy to include the working drivers???

---

