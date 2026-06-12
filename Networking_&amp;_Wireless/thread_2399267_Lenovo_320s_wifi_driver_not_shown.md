---
title: "Lenovo 320s wifi driver not shown"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by caneraydinbey on 2018-08-23
Connected Wifi shows very low signal and wifi network shows only a little wifi addresses


I have 16.04 ubuntu.


Yesterday it completely disconnected and could not reconnect to any wifi. Then somehow i managed to connect again.


Now i am connected to a wifi which is 2 meters away but it shows very low signal despite my mobile can connect with full power. And i can only see 3 wifi addresses to choose despite there are ten's of.


Those are the info:


    ~: sudo lshw -class network
      *-network               
           description: Wireless interface
           product: Qualcomm Atheros
           vendor: Qualcomm Atheros
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: wlp3s0
           version: 31
           serial: 58:00:e3:f1:10:15
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=ath10k_pci driverversion=4.15.0-32-generic firmware=WLAN.TF.1.0-00267-1 ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11
           resources: irq:127 memory:a4000000-a41fffff
    ~: 
    
    ~: lspci -knn | grep Net -A3
    03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
            Subsystem: Lenovo Device [17aa:0901]
            Kernel driver in use: ath10k_pci
            Kernel modules: ath10k_pci




I think i dont have driver here?


    Subsystem: Lenovo Device [17aa:0901]




it should show some driver of network?


What should i do?


I just installed and did once update.


When i go to additional drivers, i can only see nvidia.




     
    ~: lspci | grep Wireless




this does not bring anything

It keeps disconnectin. i have to restart always :(

---

### Post by chili555 on 2018-08-23
> wifi driver not shownThe driver is very clearly shown here:> *-network 
description: Wireless interface
product: Qualcomm Atheros
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlp3s0
version: 31
serial: 58:00:e3:f1:10:15
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="#FF0000"]driver=ath10k_pci [/COLOR]driverversion=4.15.0-32-generic firmware=WLAN.TF.1.0-00267-1 ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11
resources: irq:127 memory:a4000000-a41fffffIf there were no driver, your device would be shown as UNCLAIMED and it would not connect. You are clearly connected.

Low signal strength can be traced to a few causes. First, most Linux drivers do not like auto channel select, TKIP, etc.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Next, many routers allow raising the transmit power. Check yours.

Finally, we have seen a few cases where the antenna connections to the wireless card are not securely snapped in place. If the steps I outlined above do not help, please check yours. There are a few Linux drivers that permit antenna selection at the driver level.* ath10k_pci* is not one of them.

---

### Post by caneraydinbey on 2018-08-23
I did those steps to my country code

[COLOR=#000000]sudo iw reg set IS[/COLOR]

[COLOR=#000000]Code:
sudo nano /etc/default/crda[/COLOR]
My mobile can connect with full signal. That is why i tihnk it is about driver

---

### Post by chili555 on 2018-08-23
> sudo iw reg set ISWow! Are you actually in Iceland? I love Iceland!

Did you do each and every other step I suggested?

---

### Post by caneraydinbey on 2018-08-23
> **chili555 said:**
> Wow! Are you actually in Iceland? I love Iceland!

Did you do each and every other step I suggested?
,

No not icelan :)  tr.[ATTACH=CONFIG]280831[/ATTACH][ATTACH=CONFIG]280832[/ATTACH]

I onlt changed thouse country codes. I still try to fix modem properties.

my network disabled because of avahi. i restored to defautls.

[https://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me](https://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me)
then i made those and again i could connect

i am sending outputs of modem interface. i think no way to do better. unless i upgrade it

---

### Post by chili555 on 2018-08-23
The control channel should be fixed at 1, 6 or 11, not auto.

---

