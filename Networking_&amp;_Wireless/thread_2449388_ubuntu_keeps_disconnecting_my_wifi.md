---
title: "ubuntu keeps disconnecting my wifi"
date: 2020-08-25
forum: Networking &amp; Wireless
---

### Post by kingofswords on 2020-08-25
not sure what my  wifi is but i got this from?


06:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

---

### Post by chili555 on 2020-08-25
Please post the result of:

```
lspci -nnk | grep 0280 -A3
```Please be certain you have the correct driver installed. Here is a reference: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by kingofswords on 2020-08-27
sorry for late reply

$ lspci -nnk | grep 0280 -A3
06:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

---

### Post by chili555 on 2020-08-27
Let's dig a bit deeper:

```
dmesg | grep -e b43 -e wlp
nmcli device wifi list
```

---

### Post by kingofswords on 2020-08-27
$ dmesg | grep -e b43 -e wlp
[   13.357147] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   13.400245] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   13.400261] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2062, Revision 2, Version 0
[   23.116411] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)



$ nmcli device wifi list
IN-USE  SSID     MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       BTWi-fi  Infra  1     195 Mbit/s  57      &#9602;&#9604;&#9606;_  --


thanks.

---

### Post by chili555 on 2020-08-27
> * BTWi-fi Infra 1 195 Mbit/s 57 &#9602;&#9604;&#9606;_ --
This implies that there is *NO* encryption at all on your router.

Here is what encryption looks like:>  *       xx:2B:B0:DC:45:xx  GBR1   Infra  1     405 Mbit/s  75      &#9602;&#9604;&#9606;_  [COLOR="#FF0000"]WPA2[/COLOR]

 I doubt that your wireless driver works well with no security and I know it is quite dangerous and insecure. I suggest that you change the router to WPA2-AES, sometimes called CCMP. Do not ever use TKIP.

Also, be certain that you are using a fixed channel, not autoselect. I recommend channels 1, 6 or 11.

---

### Post by kingofswords on 2020-08-27
i dont know about all that but connection was fine before i did n update  couple days go.

---

### Post by kingofswords on 2020-08-29
Bump

---

### Post by kingofswords on 2020-08-31
Connections totally gone now, so thanks for that.

---

### Post by chili555 on 2020-08-31
> **kingofswords said:**
> Connections totally gone now, so thanks for that.
Your reply gives us precious little information to go on. Does Network Manager see your access point/router? Can you click on it and does it try to connect? What happens next? Does it just fail or does it connect for a few moments and disconnect?

May we see:

```
dmesg | grep -e b43 -e wl
nmcli device wifi list
rfkill list all

```

---

### Post by kingofswords on 2020-08-31
> **chili555 said:**
> Your reply gives us precious little information to go on. Does Network Manager see your access point/router? Can you click on it and does it try to connect? What happens next? Does it just fail or does it connect for a few moments and disconnect?

it connects like normal and even has strong signal. my phone has no problem connecting so ive been tethering via that. i have no access to router but have had no problems connecting until i did an update last week so it must be a driver issue. so dont see relevance of commands below.
...

May we see:

```
dmesg | grep -e b43 -e wl
nmcli device wifi list
rfkill list all

```
...

---

### Post by chili555 on 2020-08-31
> 
so it must be a driver issue. so dont see relevance of commands below.
You don't? b43 is, in fact, the driver. wlp or wlo is likely the interface. I think they are very relevant.

> 
it connects like normal and even has strong signal. 
Do you mean the in-built wireless device or tethering? I don't understand.

---

### Post by kingofswords on 2020-08-31
> **chili555 said:**
> You don't? b43 is, in fact, the driver. wlp or wlo is likely the interface. I think they are very relevant.

i connect BTWi-fi




$ dmesg | grep -e b43 -e wl
[   14.683915] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.461956] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   16.350657] wl 0000:06:00.0 wlp6s0: renamed from wlan0
[   20.137114] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[   20.232890] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[   21.417341] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
james@james-m:~$ nmcli device wifi list
IN-USE  SSID                      MODE   CHAN  RATE        SIGNAL  BARS  SECURIT
        TALKTALKC4BA36            Infra  1     195 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2   
        CommunityFibre10Gb_EA305  Infra  10    130 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2   
        --                        Infra  10    130 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2   
        Virgin Media              Infra  6     130 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2 80
        VM3683812                 Infra  6     130 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WP
        VM0312408                 Infra  6     130 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WP
        VM3683812_EXT             Infra  6     130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WP
        VM1989437                 Infra  11    130 Mbit/s  52      &#9602;&#9604;__  WPA1 WP
        BT-RCA6R8                 Infra  1     195 Mbit/s  49      &#9602;&#9604;__  WPA2   
        Virgin Media              Infra  11    130 Mbit/s  47      &#9602;&#9604;__  WPA2 80
        SKYBFF1F                  Infra  6     195 Mbit/s  45      &#9602;&#9604;__  WPA2   
        SKYBFF1F                  Infra  6     130 Mbit/s  45      &#9602;&#9604;__  WPA2   
        BTWifi-X                  Infra  1     195 Mbit/s  44      &#9602;&#9604;__  WPA1 WP
        BTWi-fi                   Infra  1     195 Mbit/s  44      &#9602;&#9604;__  --     
        --                        Infra  1     195 Mbit/s  44      &#9602;&#9604;__  WPA2   
        TALKTALK8EAF64            Infra  1     270 Mbit/s  37      &#9602;&#9604;__  WPA1 WP
        SKYC7414                  Infra  6     130 Mbit/s  30      &#9602;___  WPA2   
        --                        Infra  11    130 Mbit/s  29      &#9602;___  WPA2   
        VM502629-2G               Infra  1     195 Mbit/s  27      &#9602;___  WPA1 WP
        VM525891-2G               Infra  11    130 Mbit/s  27      &#9602;___  WPA1 WP
        TALKTALK4F9133            Infra  11    130 Mbit/s  22      &#9602;___  WPA1 WP
        SKY59E4F                  Infra  11    130 Mbit/s  20      &#9602;___  WPA2   
lines 1-23...skipping...
IN-USE  SSID                      MODE   CHAN  RATE        SIGNAL  BARS  SECURITY         
        TALKTALKC4BA36            Infra  1     195 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2             
        CommunityFibre10Gb_EA305  Infra  10    130 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2             
        --                        Infra  10    130 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2             
        Virgin Media              Infra  6     130 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2 802.1X      
        VM3683812                 Infra  6     130 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2        
        VM0312408                 Infra  6     130 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WPA2        
        VM3683812_EXT             Infra  6     130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2        
        VM1989437                 Infra  11    130 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2        
        BT-RCA6R8                 Infra  1     195 Mbit/s  49      &#9602;&#9604;__  WPA2             
        Virgin Media              Infra  11    130 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X      
        SKYBFF1F                  Infra  6     195 Mbit/s  45      &#9602;&#9604;__  WPA2             
        SKYBFF1F                  Infra  6     130 Mbit/s  45      &#9602;&#9604;__  WPA2             
        BTWifi-X                  Infra  1     195 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2 802.1X 
        BTWi-fi                   Infra  1     195 Mbit/s  44      &#9602;&#9604;__  --               
        --                        Infra  1     195 Mbit/s  44      &#9602;&#9604;__  WPA2             
        TALKTALK8EAF64            Infra  1     270 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2        
        SKYC7414                  Infra  6     130 Mbit/s  30      &#9602;___  WPA2             
        --                        Infra  11    130 Mbit/s  29      &#9602;___  WPA2             
        VM502629-2G               Infra  1     195 Mbit/s  27      &#9602;___  WPA1 WPA2        
        VM525891-2G               Infra  11    130 Mbit/s  27      &#9602;___  WPA1 WPA2        
        TALKTALK4F9133            Infra  11    130 Mbit/s  22      &#9602;___  WPA1 WPA2        
        SKY59E4F                  Infra  11    130 Mbit/s  20      &#9602;___  WPA2             
        VM7049365_EXT             Infra  11    130 Mbit/s  19      &#9602;___  WPA1 WPA2 

Do you mean the in-built wireless device or tethering? I don't understand.


 the in-built wireless device

---

### Post by chili555 on 2020-08-31
You said:> it connects like normal and even has strong signal.Then I asked:
> Do you mean the in-built wireless device or tethering? I don't understand.Your reply is:> 
the in-built wireless device
So if the in-built wireless device connects like normal and has strong signal, then what is the question or issue you are having?

What am I misunderstanding?

---

### Post by kingofswords on 2020-09-01
[COLOR=#000000][INDENT]So if the in-built wireless device connects like normal and has strong signal, then what is the question or issue you are having?

What am I misunderstanding?



it originally kept d/c but now just no internet[/INDENT]
[/COLOR]

---

### Post by davehk on 2020-09-01
I assume you have tried re-starting the BT Hub? They have a habit of doing this.
(possibly down to memory leaks)

---

### Post by kingofswords on 2020-09-02
> **davehk said:**
> I assume you have tried re-starting the BT Hub? They have a habit of doing this.
(possibly down to memory leaks)


no problem with hub as ive said my phone connects no problem.


<snip>

---

### Post by coffeecat on 2020-09-02
I've removed the line that did not conform to the forum Code of Conduct. Since the OP does not appear to want to follow posted advice, I've closed this thread.

Thanks to all who tried to help.

---

