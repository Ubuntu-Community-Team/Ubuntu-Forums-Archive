---
title: "Xubuntu 13.10 Wifi disconnects with closed lid..."
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by ldc2357 on 2013-12-12
Just to clear this up right now, I have gone into the power manager and set the appropriate settings. I have installed debian-based linux distros more than a few times, and thats one of the first things I do on a new installation.

What happens is: After I have told the network manager to do nothing when lid is closed, powered vs battery only etc... When I reopen the lid, it has lost the wifi connection and is restablishing the connection when I see it. Now if I can close the lid, and it just flickers, thats not the end of the world. But I often download something that takes hours to download, like wine, I prefer to close the lid.

Now I did some googling, ran some code...

```

ldc@xbox:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE403"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:51:1A:AD:F9   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:383   Missed beacon:0


```

and

```

ldc@xbox:~$ rfkill list wlan
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Power management is "off" ? Not sure what thats all about...

Kinda stabbing in the dark here, I don't really know what to do at this point (its probably and easy fix).
Any help at all is appreciated.

edit: I forgot to mention that everything else works fine, its just this one bug/problem that is giving me an issue.

---

### Post by varunendra on 2013-12-14
Please try creating a blank file in the /etc/pm/power.d/ directory to disable the default power management script that handles wireless power -
```
sudo touch /etc/pm/power.d/wireless
```
Then close the lid and see if it does the miracle. If not, reboot and try again.

If still no joy, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Along with the report, please also post -
```
cat /var/log/pm-powersave.log
```
..after the problem occurs.

---

