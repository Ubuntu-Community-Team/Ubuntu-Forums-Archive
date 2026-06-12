---
title: "Slow/weak wifi connection after upgrade from 17.10 to 18.04"
date: 2018-05-29
forum: Networking &amp; Wireless
---

### Post by arkran on 2018-05-29
[FONT=verdana]Hello there, newbie over hereAfter the system upgraded from kubuntu 17.10, i experienced a network issue where the connection is slow and it seems like signal drops from full to almost nothing sometimes.
 I don't understand why, my router is about two meters from the computer.
I tried some solutions like adding [COLOR=#000000]options ```
iwlwifi 11n_disable=8 iwlwifi bt_coex_active=0
```to [/COLOR][COLOR=#000000]/etc/modprobe.d/iwlwifi.conf but it didn't work. Also i installed wicd and didn't help either. 

Here is the log provided by the wireless script [http://paste.ubuntu.com/p/yNwY2FbTt5/](http://paste.ubuntu.com/p/yNwY2FbTt5/)
[/COLOR]Any help is greatly appreciated
Thanks![/FONT]

---

### Post by chili555 on 2018-05-29
> I tried some solutions like adding options
Code:
iwlwifi 11n_disable=8 iwlwifi bt_coex_active=0
to /etc/modprobe.d/iwlwifi.conf but it didn't work.I expect not. iwlwifi is a driver for an Intel device. You have a Mediatek: > Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter I am puzzled by this:> I don't understand why, my router is about two meters from the computer....because of this:> SSID        BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
dd-wrt      <MAC 'dd-wrt' [AN1]>  Infra  6     2437 MHz  54 Mbit/s   74      &#9602;&#9604;&#9606;_  WPA2       no             
FQS         <MAC 'FQS' [AN2]>  Infra  11    2462 MHz  270 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
Casa H197   <MAC 'Casa H197' [AN3]>  Infra  1     2412 MHz  130 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2       no             
--          <MAC '--' [AN4]>  Infra  11    2462 MHz  65 Mbit/s   69      &#9602;&#9604;&#9606;_  --         no             
Gilltosso   <MAC 'Gilltosso' [AN5]>  Infra  11    2462 MHz  130 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
KENAY       <MAC 'KENAY' [AN6]>  Infra  1     2412 MHz  270 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1       no             
ELY         <MAC 'ELY' [AN7]>  Infra  11    2462 MHz  130 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no             
Zeus        <MAC 'Zeus' [AN8]>  Infra  11    2462 MHz  270 Mbit/s  [COLOR="#FF0000"]38[/COLOR]      &#9602;&#9604;__  WPA2       yes     *      
mcampos 90  <MAC 'mcampos 90' [AN9]>  Infra  10    2457 MHz  130 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no             
But yet when the script was run, earlier in the process, this was the result:> wlp3s0f0  IEEE 802.11  ESSID:"Zeus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Zeus' [AN8]>   
          Bit Rate=150 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         [COLOR="#FF0000"] Link Quality=70/70 [/COLOR] Signal level=39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:128  Invalid misc:48   Missed beacon:0
Is your router set to auto select the channel (booooo!) or to a fixed channel; 1, 6 or 11 (preferred)?

Is your router defective? Do the symptoms go away temporarily if you power-cycle the router?

---

### Post by arkran on 2018-05-29
Thanks for the quick response chili555

> 
[COLOR=#000000]I expect not. iwlwifi is a driver for an Intel device. You have a Mediatek
[/COLOR]
Ignorance at its finest. My bad, I removed it, but i suspect that this won't make difference as is not intended for this card.

After removing it, seems like wifi signal is not drooping anymore. However the network bandwidth is still slow, i think this is not an issue with the router,
it happened the same today at my workplace

> [COLOR=#000000]Is your router set to auto select the channel (booooo!) or to a fixed channel; 1, 6 or 11 (preferred)?[/COLOR]

I'll take the booo! option, it's set in auto mode. Gonna look for info on how to choose the best channel

> [COLOR=#000000][INDENT]Is your router defective? Do the symptoms go away temporarily if you power-cycle the router?
[/INDENT]
[/COLOR]


No, other devices works fine with it, my laptop has a dual boot, the wifi connection is fine on windows

---

### Post by chili555 on 2018-05-30
>  it's set in auto mode. Gonna look for info on how to choose the best channelHere is a long thread on why auto select is a very bad idea. [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)  Many Linux wireless drivers, most, probably, are very troubled by the attempt to connect to and follow an ever-moving target. I recommend channels 1, 6 or 11: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html)

---

