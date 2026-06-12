---
title: "Madwifi problems"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by new_11 on 2007-12-18
I've looked in many other threads, but am having trouble finding an answer to my issue.
I'm using a macbook pro (nvidia 8600), and my issue is with wireless. I downloaded and compiled the latest version of madwifi and installed it. My wireless works beautifully for a little while, but soon, Network Manager says "No network devices have been found". 
I ran the network manager with nm-applet --no-daemon, and it gives this error :

process : arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.

(It gives this error repeatedly, maybe 5-6 times before eventually barfing)

I have another laptop that i use (with the infamous broadcom chip), and that has the EXACT same issue (works, then stops, and says No network devices have been found). I am unable to figure this out. 

lspci output:
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
iwconfig output :
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point:   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-76 dBm  Noise level=-96 dBm
          Rx invalid nwid:13683  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


note : iwlist scan usually identifies that networks CAN be found (after network manager goes crazy). And also, this is extremely detrimental to my work, cause it pegs one CPU to 100%. 

I'm running 7.10 fully updated etc (This happens with a clean install as well, and with the madwifi-ng driver as well. I've tried various snapshots as well as the latest code from svn. nothing works!).
Any help would be appreciated. thanks in advance.

---

### Post by Junglizer on 2007-12-19
I've sent you a PM.

---

