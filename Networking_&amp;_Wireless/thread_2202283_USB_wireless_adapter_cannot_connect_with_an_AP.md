---
title: "USB wireless adapter cannot connect with an AP"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by ryan43 on 2014-01-28
I have a opam5 development board which has already install ubuntu 12.04, I laptop is ubuntu 12.04 as well, I build an AP on my laptop and use some devices like mobile, other laptop to check whether the AP work well. And they can connect and browse the internet pages. There is not a wlan card on the development board, so I use USB wireless adapter and install some necessary modules
```
lsmod
arc4                              1659  2                                                                  
rtl8192cu                      88772  0                                                                  
rtlwifi                            79854  1 rtl8192cu                                                        
rtl8192c_common        60914  1 rtl8192cu                                                        
mac80211                    458124  3 rtl8192cu,rtlwifi,rtl8192c_common                                
cfg80211                     434462  2 rtlwifi,mac80211                                                 
snd_soc_spdif_tx        1383  0                                                                  
snd_soc_omap_abe_twl6040    18349  1                                                             
snd_soc_twl6040        21319  1 snd_soc_omap_abe_twl6040                                         
snd_soc_omap            3133  1                                                                  
snd_soc_omap_mcpdm      5968  0                                                                  
snd_soc_omap_abe       38413  3 snd_soc_omap_abe_twl6040,snd_soc_omap_mcpdm                      
snd_soc_abe_hal        39966  2 snd_soc_omap_mcpdm,snd_soc_omap_abe                              
snd_soc_omap_dmic       5299  0                                                                  
snd_soc_omap_mcbsp     21922  1 snd_soc_omap_abe_twl6040                                         
snd_soc_omap_mcasp      5479  0                                                                  
omapdce                          21996  0                                                                  
virtio_rpmsg_bus               11153  1 omapdce                                                          
omap_remoteproc             3034  0                                                                  
remoteproc                      25221  1 omap_remoteproc  

```

then I use command: ifconfig wlan0 up 
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 4a:af:4a:e3:7b:ad                                          
          inet addr:10.5.68.55  Bcast:10.5.69.255  Mask:255.255.254.0                            
          inet6 addr: fe80::48af:4aff:fee3:7bad/64 Scope:Link                                    
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                     
          RX packets:31530 errors:0 dropped:0 overruns:0 frame:0                                 
          TX packets:422 errors:0 dropped:0 overruns:0 carrier:0                                 
          collisions:0 txqueuelen:1000                                                           
          RX bytes:6732762 (6.7 MB)  TX bytes:43962 (43.9 KB)                                    
                                                                                                 
lo        Link encap:Local Loopback                                                              
          inet addr:127.0.0.1  Mask:255.0.0.0                                                    
          inet6 addr: ::1/128 Scope:Host                                                         
          UP LOOPBACK RUNNING  MTU:65536  Metric:1                                               
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                     
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                   
          collisions:0 txqueuelen:0                                                              
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                 
                                                                                                 
wlan0     Link encap:Ethernet  HWaddr ec:1a:59:d5:4e:e3                                          
          inet addr:169.254.88.190  Bcast:169.254.255.255  Mask:255.255.0.0                      
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                             
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                     
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                   
          collisions:0 txqueuelen:1000                                                           
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

but the problem is when I use command:
```
iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

```
iwconfig
wlan0     no wireless extensions.                                                                
                                                                                                 
sit0      no wireless extensions.                                                                
                                                                                                 
lo        no wireless extensions.                                                                
                                                                                                 
eth0      no wireless extensions.
```

then I found I can use iw wlan0 scan to search the wifi and use command
```
iw wlan0 connect peipei keys 0:0123456789
```
and check
```
iw wlan0 link
Connected to 60:67:20:9a:8a:30 (on wlan0)                                                        
        SSID: peipei                                                                             
        freq: 2457                                                                               
        RX: 2620 bytes (74 packets)                                                              
        TX: 742 bytes (6 packets)                                                                
        signal: -68 dBm                                                                          
        tx bitrate: 18.0 MBit/s                                                                  
                                                                                                 
        bss flags:      short-slot-time                                                          
        dtim period:    0                                                                        
        beacon int:     100          

```
then I tried to connect internet like google, but the page cannot open, so what is wrong with my step?
Thanks

---

### Post by praseodym on 2014-01-28
Hi,

update the driver via LAN:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot.

---

