---
title: "Define kismet (config) source."
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by soeten on 2007-08-17
Hey, Ive been trying to install kismet in ubuntu for a while now but I cant seem to get the SOURCE in kismet.conf correct. : S

```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=**none,none,addme**
```

iwconfig output:
```
psycho@Psy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=6/94  Signal level=-90 dBm  Noise level=-96 dBm
          Rx invalid nwid:28935  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=6/94  Signal level=-90 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I dont really know exactly what model the wifi card is other than its supposed to be a Atheros 802.11b, 802.11g card, since its been working right out of the box in Back|Track2 (livecd with tools such as kismet, aircrack etc.) Ive been reading the kismet documentation trying to figure out exactly what to write without any luck. : (

Thanks in advance, I really hope anyone can help me.

---

### Post by little dave on 2007-09-22
> **soeten said:**
> Hey, Ive been trying to install kismet in ubuntu for a while now but I cant seem to get the SOURCE in kismet.conf correct. : S

```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=**none,none,addme**
```

iwconfig output:
```
psycho@Psy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=6/94  Signal level=-90 dBm  Noise level=-96 dBm
          Rx invalid nwid:28935  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=6/94  Signal level=-90 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I dont really know exactly what model the wifi card is other than its supposed to be a Atheros 802.11b, 802.11g card, since its been working right out of the box in Back|Track2 (livecd with tools such as kismet, aircrack etc.) Ive been reading the kismet documentation trying to figure out exactly what to write without any luck. : (

Thanks in advance, I really hope anyone can help me.

Better late then never. 

 Try   
 ```
source=madwifi_b,wifi0,laptop card  
```

The "laptop card" can be what you want. I use it to tell me its the wireless card in my laptop. <simple right?>

---

