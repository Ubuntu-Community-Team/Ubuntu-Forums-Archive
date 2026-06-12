---
title: "I want to install my Wayona WiFi Adaptor and start the hotspot"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by gautam5 on 2016-01-31
I bought a new WiFi adaptor - Wayona Wireless Mini WiFi Adaptor ([http://www.amazon.in/Wayona-WYN-12-150Mbps-Wireless/dp/B00M3AXOD0/ref=pd_cp_147_2](http://www.amazon.in/Wayona-WYN-12-150Mbps-Wireless/dp/B00M3AXOD0/ref=pd_cp_147_2)) because the wifi range and strength of its (ubuntu's) own hotspot is very POOR.
I tried installing in windows and its really very easy (click the setup, install driver, install utility software and you are done! ) but i want to install it to my Ubuntu ( 15.10 ). I have read a lot of documentations and a lot of solutions but none of them worked right.

The contents of the driver CD corresponding to linux are (which I presume as drivers) - 
1. DPA_MT7601U_LinuxSTA_3.0.0.4_20130916
2. DPA_RT5572_LinuxSTA_2.6.1.4_20121211
3. MT7601U_LinuxAP_3.0.0.1_20130802
4. RT5572_RT5372_Linux_AP_V2.7.1.1_Beta_DPA_20121113
And a folder "DOC"
([COLOR=#333333][FONT=verdana]Drivers available at below link : [http://goo.gl/mR7PgO](http://goo.gl/mR7PgO)[/FONT][/COLOR])

I can't understand the installation procedure as given in the guide as it is too lengthy and also I don't know much about linux systems.
Please help me how to install the driver, then how to configure the system, and finally how to start & stop the HOTSPOT !


Thanks in advance :)
(P.S. - I bought this just because Linux was supported in its specifications, and I want to make my laptop as a HOTSPOT in Ubuntu so that I "#STICK" to ubuntu and #explore it)

---

### Post by praseodym on 2016-02-01
Hi,

to know which driver is the correct one, plug in the stick, open a terminal with CTRL+ALT+T and show the output of these commands
```

lsusb
usb-devices
lsmod
```

---

