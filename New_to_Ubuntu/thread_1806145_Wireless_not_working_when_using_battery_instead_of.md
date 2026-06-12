---
title: "Wireless not working when using battery instead of mains"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by redanast on 2011-07-17
Hi,

I recently installed Ubuntu 11.04 on a Asus eee and its amazing, but I have the following problem with the wireless. It seems to work only when the computer is connected to mains. As soon as it is on battery supply the wireless disconnects.
Any ideas? I checked the power management but the options were limited.

Thanks

---

### Post by Wim Sturkenboom on 2011-07-17
Just shouting something

Any options in the BIOS that will disable the wireless when running on battery?

---

### Post by bkratz on 2011-07-17
> **redanast said:**
> Hi,

I recently installed Ubuntu 11.04 on a Asus eee and its amazing, but I have the following problem with the wireless. It seems to work only when the computer is connected to mains. As soon as it is on battery supply the wireless disconnects.
Any ideas? I checked the power management but the options were limited.

Thanks

Please look at the output (and post)  of 

iwconfig

and see if it says  "power management on" or not

---

### Post by redanast on 2011-07-17
Hi 

Thanks for the prompt reply. It looks like the power management is on:
[I]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub2-4F9S"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:4E:55:A7:C8   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:39   Missed beacon:0[/I]

Is there any way I can turn it off?

Thanks again for the help.

---

### Post by bkratz on 2011-07-17
> **redanast said:**
> Hi 

Thanks for the prompt reply. It looks like the power management is on:
[I]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub2-4F9S"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:4E:55:A7:C8   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:39   Missed beacon:0[/I]

Is there any way I can turn it off?

Thanks again for the help.


Should just be a simple

sudo iwconfig wlan0 power off

See in terminal   

  man iwconfig

manual stands for manual, there is all kinds of options

---

### Post by renzokuken on 2011-07-18
maybe this might shed some light

[http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67)

not sure if its Mac specific though

---

### Post by amjjawad on 2011-07-18
Some [Googlubuntu ]("http://www.googlubuntu.com/")search found:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Wireless+not+working+when+using+battery+instead+of+mains+&as_qdr=all&sa=Google+Search&lang=en#1397](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Wireless+not+working+when+using+battery+instead+of+mains+&as_qdr=all&sa=Google+Search&lang=en#1397)

---

### Post by redanast on 2011-07-18
Hi 

Thanks again for the help. I tried the sudo iwconfig wlan0 power off command and it does turn the power management off, but the wireless still does not come on. I tried restarting as well but this resulted in the power management to turn on again.

---

