---
title: "how to install driver+software from cd"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by wanakev2 on 2010-06-08
hello forumers,

recently, i just bought a wifly-city 8g wifi booster for my laptop. i want to run it on ubuntu. the wireless usb adapter come up with a driver+software cd. sadly, i dunno where to start for installing the driver. anyone can show me the steps? (im totally new to linux os)

file that given in the cd
[IMG]http://i845.photobucket.com/albums/ab12/wanakev2/Screenshot1.png[/IMG]

and here what written in the read me file,
```
Release Date: 2006-02-09, ver 1.2 
RTL8187 Linux driver version 1.2 
 
   --This driver supports RealTek RTL8187 Wireless LAN driver for  
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006,  
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc. 
   - Support Client mode for either infrastructure or adhoc mode 
   - Support WEP and WPAPSK connection 
 
< Component > 
The driver is composed of several parts: 
    1. Module source code 
      stack.tar.gz 
      drv.tar.gz 
     
    2. Script ot build the modules 
      makedrv 
 
    3. Script to load/unload modules 
      wlan0up 
      wlan0down  
 
    4. Script and configuration for DHCP 
       wlan0dhcp 
      ifcfg-wlan0 
    4. Supplicant source code: 
      wpa_supplicant-0.4.9.tar.gz 
 
    5. Example of supplicant configuration file: 
      wpa1.conf 
 
< Installation > 
Runing the scripts can finish all operations of building up modules  
from the source code and start the nic. 
    1. Build up the drivers from the source code 
      ./makedrv 
 
    2. load the driver module to kernel and start up nic 
      ./wlan0up 
 
< Set wireless lan MIBs > 
This driver uses Wireless Extension as an interface allowing you to set 
Wireless LAN specific parameters. 
 
Current driver supports "iwlist" to show the device status of nic 
        iwlist wlan0 [parameters] 
where 
        parameter explaination          [parameters]     
        -----------------------         -------------    
        Show available chan and freq    freq / channel   
        Show and Scan BSS and IBSS     scan[ning]           
        Show supported bit-rate         rate / bit[rate]         
        Show Power Management mode      power              
 
For example: 
    iwlist wlan0 channel 
    iwlist wlan0 scan 
    iwlist wlan0 rate 
    iwlist wlan0 power 
 
Driver also supports "iwconfig", manipulate driver private ioctls, to set 
MIBs. 
 
    iwconfig wlan0 [parameters] [val] 
where 
    parameter explaination      [parameters]        [val] constraints 
        -----------------------     -------------        ------------------ 
        Connect to AP by address    ap                  [mac_addr] 
        Set the essid, join (I)BSS  essid                 [essid] 
        Set operation mode          mode                {Managed|Ad-hoc} 
        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off} 
 
For example: 
    iwconfig wlan0 ap XX:XX:XX:XX:XX:XX 
    iwconfig wlan0 essid "ap_name" 
    iwconfig wlan0 mode Ad-hoc 
    iwconfig wlan0 mode essid "name" mode Ad-hoc 
    iwconfig wlan0 key 0123456789 [2] open 
    iwconfig wlan0 key off 
    iwconfig wlan0 key restricted [3] 0123456789 
 
< Getting IP address > 
After start up the nic, the network needs to obtain an IP address before 
transmit/receive data. 
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS" 
command, or using DHCP. 
 
If using DHCP, setting steps is as below: 
    (1)connect to an AP via "iwconfig" settings 
        iwconfig wlan0 essid [name]    or 
        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX 
 
    (2)run the script which run the dhclient 
        ./wlan0dhcp 
           or  
        dhcpcd wlan0 
                  (Some network admins require that you use the 
                  hostname and domainname provided by the DHCP server. 
                  In that case, use  
        dhcpcd -HD wlan0) 
         
< WPAPSK > 
WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK 
mechanism 
     
    (1)Unpack source code of WPA supplicant: 
      tar -zxvf wpa_supplicant-0.4.9.tar.gz 
      cd wpa_supplicant-0.4.9 
     
    (2)Create .config file: 
      cp defconfig .config 
     
    (3)Edit .config file, uncomment the following line: 
      #CONFIG_DRIVER_IPW=y. 
         
    (4)Build WPA supplicant: 
      make 
    If make error for lack of <include/md5.h>, install the openssl lib(two ways): 
     1. Install the openssl lib from corresponding installation disc: 
        Fedora Core 2/3/4/5(openssl-0.9.71x-xx), Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk), 
        Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), Gentoo(dev-libs/openssl), etc. 
     2. Download the openssl open source package from www.openssl.org, build and install it. 
      
    (5)Edit wpa_supplicant.conf to set up SSID and its passphrase. 
      For example, the following setting in "wpa1.conf" means SSID  
          to join is "BufAG54_Ch6" and its passphrase is "87654321". 
      network={ 
            ssid="BufAG54_Ch6" 
            proto=WPA 
            key_mgmt=WPA-PSK 
            pairwise=CCMP TKIP 
            group=CCMP TKIP WEP104 WEP40 
            psk="87654321" 
            priority=2 
          } 
 
    (6)Execute WPA supplicant (Assume 8187 and related modules had been 
           loaded): 
      ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &
```

anyone?:(

---

### Post by cariboo on 2010-06-09
All you have to do is plug your device in, it should be automagically detected and the driver loaded. To check open a terminal after you plug in the device and type:

```
dmesg | tail -n15
```

the output should look something like this:

```
dmesg | tail -n15
[24505.530028] usb 1-8: new high speed USB device using ehci_hcd and address 3
[24506.060050] cfg80211: Calling CRDA to update world regulatory domain
[24506.245621] cfg80211: World regulatory domain updated:
[24506.245625]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[24506.245629]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[24506.245632]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[24506.245635]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[24506.245637]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[24506.245640]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[24506.478133] phy0: Selected rate control algorithm 'minstrel'
[24506.478853] Registered led device: rt73usb-phy0::radio
[24506.478870] Registered led device: rt73usb-phy0::assoc
[24506.478890] Registered led device: rt73usb-phy0::quality
[24506.479352] usbcore: registered new interface driver rt73usb
[24507.201954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

to check if the driver is properly loaded, in the same terminal type:

```
sudo lshw -C network
```

the output should look something like this:

```
sudo lshw -C network
[sudo] password for me: 
  *-network:0 DISABLED    
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:8
       logical name: **wlan0**
       serial: 00:1c:f0:a3:ca:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=rt73usb** driverversion=2.6.35-1-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

Look for wlan0 and driver, I bolded the two in the example above.

---

### Post by HyperSha on 2010-06-20
hi guys, 
i'm having a trouble with Wifly-City G8 with my ubuntu, i don't know if you guys are having the same problem? or not.
when i first plugged the device, it started to work properly. i got connected to a wireless internet, but after several seconds, the internet stops responding. even thought the connection link shows full, but there is no internet. i try to use my laptops local wireless, and everything works fine. i tried to install the driver from the CD, but i'm having problems. frankly i don't know how to install the driver, can you guys give me a hint how to install the driver? 
thank you

---

