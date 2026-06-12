---
title: "Wifi keeps asking for password"
date: 2022-07-04
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2022-07-04
Hi, this happened out of the blue, wifi suddenly stopped working this afternoon. Haven't done any upgrade, haven't rebooted.
It suddenly stopped connecting and kept asking for password, then after I autenticated it will connect for a few seconds and disconnect and ask for password again, then it will stop working altogether. On reboot it works for may be 5 or 10 minutes and then it happens again.


System is Ubuntu 20.04

```


 sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:6d:00.1
       logical name: enp109s0f1
       version: 12
       serial: 80:fa:5b:4a:fa:fb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.17.5-76051705-generic firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:d000(size=256) memory:dc304000-dc304fff memory:dc300000-dc303fff
  *-network
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:6e:00.0
       logical name: wlp110s0
       version: 78
       serial: ac:ed:5c:ba:28:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.17.5-76051705-generic firmware=36.ca7b901d.0 8265-36.ucode ip=192.168.2.143 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:138 memory:dc200000-dc201fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:9a:68:17
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```

```


sudo dmesg | tail
wlp110s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 66:99:61:b9:12:95
wlp110s0: deauthenticated from 66:99:61:b9:12:95 (Reason: 2=PREV_AUTH_NOT_VALID)

```

But the password hasn't changed.

```

iwconfig
lo        no wireless extensions.

enp109s0f1  no wireless extensions.

wlp110s0  IEEE 802.11  ESSID:"BELL132"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 6C:99:61:B9:12:96   
          Bit Rate=300 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

virbr0    no wireless extensions.

virbr0-nic  no wireless extensions.


```
 

Please help. Thanks.

---

### Post by chili555 on 2022-07-05
Please note:

> wlp110s0: deauthenticated from 66:99:61:b9:12:[COLOR="#FF0000"]95 [/COLOR]

And also:

> wlp110s0  IEEE 802.11  ESSID:"BELL132"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 6C:99:61:B9:12:[COLOR="#FF0000"]96  [/COLOR] 

I am quite confident that these are the 2.4 gHz and 5 gHz segments of your router. Your wireless is roaming from between them looking for a better connection, much like my ex-girlfriend.

Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

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

-------------------------------

Useful information: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

---

### Post by monkeybrain20122 on 2022-07-05
Hi, Chilli555,

I had to wait for my roommate to come home since I have no access to router. He just restarted the router and it has been  working for a few hours now. Not sure what has happened, he told me he never changed the settings. I will mark this thread as solved now.


Thanks for the detailed reply. I will keep it for future references

---

### Post by kurt18947 on 2022-07-06
> **monkeybrain20122 said:**
> Hi, Chilli555,

I had to wait for my roommate to come home since I have no access to router. He just restarted the router and it has been  working for a few hours now. Not sure what has happened, he told me he never changed the settings. I will mark this thread as solved now.


Thanks for the detailed reply. I will keep it for future references

Do you know if the router has any sort of auto restart? DD-WRT does and I have my main router set to reboot once per week when I'm pretty sure I won't using it.

---

