---
title: "Where is the inf file located?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by WinterWoodlands on 2010-01-07
I have tried searching for it, but I cannot find it.  As I have installed Ubuntu on my laptop, I would like to use a wireless connection.

Computer Model: Toshiba Satellite
Router Model: Linksys WRT54G

Please keep in mind that I am new to Ubuntu.

---

### Post by running_rabbit07 on 2010-01-07
Network Manager should be able to connect you. Right click the Ethernet icon in the upper right corner.

---

### Post by WinterWoodlands on 2010-01-07
I have tried many times to connect to the wireless network.  It is protected, but I know the password, having set it myself, yet it will not connect.  It will try, then ask me for the code to connect to the wireless again.  It does this every time.

I am trying to use the driver, and have been following the troubleshooting steps, and am currently at the step where it asks me for the inf file, but I cannot locate it.  I just need to know where to look on the computer for this file, so I can continue to set up the wireless driver.

---

### Post by bodhi.zazen on 2010-01-07
Your router should not matter, although rarely they do.

What wireless card do you have ?

Are you using WEP or WPA ?

What version of Ubuntu ?

The INF file is if you are trying to install windows driver.

Open a terminal and show us the output of ```
iwconfig
```

---

### Post by WinterWoodlands on 2010-01-07
WPA, and the newest version of Ubuntu.

I am really not very good with this kind of this, I guess. xD  Sorry I`m so clueless.

**Edit:** Output is:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I am currently using the ethernet cable to connect to the internet on my laptop, in case that affects the results of this...

---

### Post by Methuselah on 2010-01-07
Make sure the dropdown box says WPA when you're entering the password.
Usually it selects the right authentication scheme but just confirm.

---

### Post by WinterWoodlands on 2010-01-07
WPA & WPA2 Personal is what is selected when I try to connect.

---

### Post by bodhi.zazen on 2010-01-07
Your wireless card is working, so you do not need to install the INF, lol.

The next step is to turn off WPA and try to connect. If you can connect then the issue is with WPA.

---

### Post by Methuselah on 2010-01-07
Watch out for CAPS lock!
I know, I'm really reaching but it seems that if you can see networks your card is working to some extent.

---

