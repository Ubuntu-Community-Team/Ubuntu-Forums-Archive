---
title: "Killer Wi-Fi 6 AX1650i 160MHz Wireless- dropping after modem replacement"
date: 2020-10-18
forum: Networking &amp; Wireless
---

### Post by n36078 on 2020-10-18
My ISP sent me a new modem as part of their random troubleshooting of a time of day slowdown.  They went from Netgear 7750 to Arris NVG433B.  Since then my Asus Vivobook15 has been dropping the wifi connection every 10-20 minutes  I usually just turn off and on wifi to reconnect.  This also used to happen occasionally on the Netgear router but no where near as often - maybe once or twice a day.  

I am thinking it is a driver problem but don't know what driver to use or the current driver can't handle whatever wifi spec the modem is picking.  

I found a lot of complaints and questions about the Killer AX1650 but nobody claiming a solution.  Running 20.04 updated yesterday.

The bottom lines of dmesg -r after a retart of the wifi shows:

<6>[  540.656574] wlo1: Connection to AP a8:97:cd:c9:4e:44 lost
<6>[  540.952232] wlo1: send auth to a8:97:cd:c9:4e:44 (try 2/3)
**<3>[  541.566668] iwlwifi 0000:00:14.3: No beacon heard and the time event is over already...**
<6>[  541.566747] wlo1: Connection to AP a8:97:cd:c9:4e:44 lost
<6>[  541.976270] wlo1: send auth to a8:97:cd:c9:4e:44 (try 3/3)
**<3>[  542.590737] iwlwifi 0000:00:14.3: No beacon heard and the time event is over already...**
<6>[  542.590815] wlo1: Connection to AP a8:97:cd:c9:4e:44 lost
<6>[  542.967785] wlo1: authentication with a8:97:cd:c9:4e:44 timed out
<6>[  550.725663] wlo1: authenticate with a8:97:cd:c9:4e:44
<6>[  550.726992] wlo1: send auth to a8:97:cd:c9:4e:44 (try 1/3)
<6>[  550.747887] wlo1: authenticated
<6>[  550.751987] wlo1: associate with a8:97:cd:c9:4e:44 (try 1/3)
<6>[  550.753102] wlo1: RX AssocResp from a8:97:cd:c9:4e:44 (capab=0x1011 status=0 aid=3)
<6>[  550.755704] wlo1: associated
<6>[  550.770140] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
<7>[  550.787276] wlo1: Limiting TX power to 24 (24 - 0) dBm as advertised by a8:97:cd:c9:4e:44
dave@vivobook:~$ 


I have changed the beacon interval on the modem from 100ms to 75ms but no change.


 dave@vivobook:~$ uname -r
 5.4.0-47-generic
 dave@vivobook:~$  
 
 
 dave@vivobook:~$ sudo lshw -C network
 [sudo] password for dave:  
   *-network                  
        description: Wireless interface

        **product: Killer Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter (201NGW)**

        vendor: Intel Corporation

        physical id: 14.3
        bus info: pci@0000:00:14.3
        logical name: wlo1
        version: 30
        serial: 08:d2:3e:d9:34:c9
        width: 64 bits

        clock: 33MHz
        capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes **driver=iwlwifi driverversion=5.4.0-47-generic** firmware=48.4fa0041f.0 ip=192.168.254.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11
        resources: iomemory:600-5ff irq:16 memory:6001124000-6001127fff
 dave@vivobook:~$  
 
 
 
 
 
 
 dave@vivobook:~$ lspci
 00:00.0 Host bridge: Intel Corporation Device 8a02 (rev 03)
 00:02.0 VGA compatible controller: Intel Corporation Device 8a56 (rev 07)
 00:04.0 Signal processing controller: Intel Corporation Device 8a03 (rev 03)
 00:14.0 USB controller: Intel Corporation Ice Lake-LP USB 3.1 xHCI Host Controller (rev 30)
 00:14.2 RAM memory: Intel Corporation Device 34ef (rev 30)
 **00:14.3 Network controller: Intel Corporation Killer Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter (201NGW) (rev 30)**

 00:14.5 SD Host controller: Intel Corporation Ice Lake-LP SD Controller (rev 30)
 00:15.0 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #0 (rev 30)

 00:15.1 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #1 (rev 30)
 00:16.0 Communication controller: Intel Corporation Management Engine Interface (rev 30)
 00:17.0 SATA controller: Intel Corporation Ice Lake-LP SATA Controller [AHCI mode] (rev 30)
 00:1d.0 PCI bridge: Intel Corporation Device 34b4 (rev 30)
 00:1e.0 Communication controller: Intel Corporation Ice Lake-LP Serial IO UART Controller #0 (rev 30)
 00:1e.2 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO SPI Controller #0 (rev 30)
 00:1f.0 ISA bridge: Intel Corporation Ice Lake-LP LPC Controller (rev 30)
 00:1f.3 Audio device: Intel Corporation Smart Sound Technology Audio Controller (rev 30)
 00:1f.4 SMBus: Intel Corporation Ice Lake-LP SMBus Controller (rev 30)
 00:1f.5 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP SPI Controller (rev 30)
 01:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2018/PC SN520 NVMe SSD (rev 01)

 
 
  
 ave@vivobook:~$ nmcli device show
 GENERAL.DEVICE:                         wlo1
 GENERAL.TYPE:                           wifi
 GENERAL.HWADDR:                         08:D2:3E:D9:34:C9
 GENERAL.MTU:                            1500
 GENERAL.STATE:                          100 (connected)
 GENERAL.CONNECTION:                     Frontier0112
 GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveC>
 IP4.ADDRESS[1]:                         192.168.254.10/24
 IP4.GATEWAY:                            192.168.254.254
 IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.254.254, >
 IP4.ROUTE[2]:                           dst = 192.168.254.0/24, nh = 0.0.0.0, m>
 IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt >
 IP4.DNS[1]:                             192.168.254.254
 IP4.DOMAIN[1]:                          frontierlocal.net
 IP6.ADDRESS[1]:                         fe80::2cfd:8137:737a:d11/64
 IP6.GATEWAY:                            --
 IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 600
 IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, tabl>
 
 
 GENERAL.DEVICE:                         p2p-dev-wlo1
 GENERAL.TYPE:                           wifi-p2p
 GENERAL.HWADDR:                         (unknown)
 GENERAL.MTU:                            0
 GENERAL.STATE:                          30 (disconnected)
 GENERAL.CONNECTION:                     --
 GENERAL.CON-PATH:                       --
 
 
 GENERAL.DEVICE:                         lo
 GENERAL.TYPE:                           loopback
 GENERAL.HWADDR:                         00:00:00:00:00:00
 GENERAL.MTU:                            65536

 GENERAL.STATE:                          10 (unmanaged)
 GENERAL.CONNECTION:                     --
 GENERAL.CON-PATH:                       --
 IP4.ADDRESS[1]:                         127.0.0.1/8
 IP4.GATEWAY:                            --
 IP6.ADDRESS[1]:                         ::1/128
 IP6.GATEWAY:                            --
 IP6.ROUTE[1]:                           dst = ::1/128, nh = ::, mt = 256
 
 
 
 
 NAME          UUID                                  TYPE  DEVICE  
 **Frontier0112  72940779-e9d0-49d1-a958-79023cfc36c1  wifi  wlo1    **

 Beagle        d4a787ac-4dad-45cf-83e8-60b23212617c  wifi  --      
 dave@vivobook:~$

---

### Post by chili555 on 2020-10-18
Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable pwer saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddnely changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

