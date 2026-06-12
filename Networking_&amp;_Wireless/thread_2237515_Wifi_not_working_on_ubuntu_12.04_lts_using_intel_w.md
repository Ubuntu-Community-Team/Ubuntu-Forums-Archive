---
title: "Wifi not working on ubuntu 12.04 lts using intel wifi link 5100"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by Mohit_Jain on 2014-08-02
Hi I am new to ubuntu and I am unable to use my wifi network on it, however it is working fine on windows. Also wired connection is working fine in ubuntu, it is just wifi that is causing trouble. I am posting below some of the outputs through which you can see specifications of device.

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:a6:b8:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=8.83.5.1 build 33692 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f8000000-f8001fff

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"RAJAT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:57:DD:F0:ED   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-13 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I am unable to figure out what is wrong. I read many answers but could not find a solution till now. Any help would be greatly appreciated.

Thanks
Mohit

---

### Post by varunendra on 2014-08-02
Welcome to the forums Mohit! :)

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

