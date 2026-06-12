---
title: "Unable to get USB wireless adapter (RTL8192USB) to function Ubuntu 10.04"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by Azpedey on 2014-04-26
Hi, everyone.   Short history;  onboard WiFi card failed, removed card from motherboard, installed USB WiFi adapter, unable to get it to work with 10.04LTS.

Computer:  HP s5730y, AMD 64bit, dual boot Ubuntu 10.04LTS and Ubuntu 12.04LTS

USB adapter uses RTL8191SU chip.  Works fine with 12.04LTS but will not work with 10.04LTS.  Have tried many, many different suggestions from this forum with no results (too many to list).  The things I have tried which may be significant are:

1.  Created folder in /lib/firmware named RTL8192SU and copied rtl8192sfw.bin into folder

2.  Used following from forum and have attached result to this post

     ```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script

```

Additional information:

```
azpedey@HPPavillion:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n ...  ESSID:"pedeynet"  
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:144.5 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
azpedey@HPPavillion:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0235 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0118 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any suggestions would be much appreciated.

---

### Post by varunendra on 2014-04-28
I didn't take a look at the report you attached, seeing how outdated 10.04 now is, and there is probably no point in wasting time on it unless you have a very specific and good reason to still stick with it.

So.. why do you want to use 10.04 when it (the desktop version) has reached its "[End of Life]("https://wiki.ubuntu.com/Releases")" long ago and no more updates are released to support it? Especially when you have a working 12.04 installation on the same system?

---

### Post by Azpedey on 2014-04-28
varunendra, thank you for your response.  My desire to continue with 10.04 is that I have used it for several years, am familiar with the desktop, and, at age 75 am not as quick to adapt to different OS's.  I have downloaded and tried several different variations of Lunux, including 12.04 Ubuntu, but have not found any with the similiar desktop.  I don't know if that is compelling enough, but I thought I would ask for help to see if I could keep what I am familiar with.

---

### Post by varunendra on 2014-04-28
I would be glad to help with whatever I can, but have you taken a look at Xubuntu yet?

If you have a fast enough Internet connection, I suggest to download its ISO and try it in Live mode. It's menu system is traditional desktop like, and many people like it over default Ubuntu for the way of its working.

I'll take a look at the wireless_script report you posted as soon as I get enough time to analyse it, and shall post back whatever suggestion I could come up with.

**PS:**
In the meanwhile, if anyone reading this thread has any ideas about the problem, please feel free to join and share it with us.

---

