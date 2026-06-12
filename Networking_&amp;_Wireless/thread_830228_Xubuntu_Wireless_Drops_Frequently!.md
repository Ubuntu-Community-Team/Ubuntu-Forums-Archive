---
title: "Xubuntu Wireless Drops Frequently!"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-06-15
Hi,
I have a:
Packard Bell Imedia NEC P700401825:
2.40 gigahertz Intel Pentium 4
256 MB of RAM
SiS 650(32 MB) Video Card
60 GB HDD

I have Xubuntu installed on it. I used the Windows drivers for my D-Link DWL-G122 Wireless Adaptor. In NDISWrapper it says 'Hardware Present: yes'. I can access the internet but it frequently drops. I used the exact same method for my Ubuntu pc and the wireless connection is flawless.

What other step must I take to have a smooth wireless internet connection on my Xubuntu Packard Bell pc? Please help. Thanks.

Just one more note: Everything else on my Packard Bell pc works perfectly!

---

### Post by Rytron on 2008-07-01
Any suggestions?

---

### Post by prshah on 2008-07-01
> **Rytron said:**
> 
I have Xubuntu installed 
 I used the Windows drivers for my D-Link DWL-G122 Wireless Adaptor.
I can access the internet but it frequently drops.


Try using the following commands to turn off power management for your wireless:```

sudo iwconfig eth9 txpower fixed
sudo iwconfig eth9 power off
sudo iwconfig eth9 commit
```

Replace "eth9" with the actual name of your wireless interface.

The third command may give an error as "feature not supported" that can be ignored.

Either one of the first two commands should work and will take effect immediately, _until_ your next reboot. 

So give the commands, then surf for an hour or two to check if it is effective. If it is effective, you can add the commands to your "/etc/rc.local" to take effect on every reboot.

Note that in the rc.local file, the last line should not be disturbed (ie, "exit 0")

---

### Post by Rytron on 2008-07-01
> **prshah said:**
> Try using the following commands to turn off power management for your wireless:```

sudo iwconfig eth9 txpower fixed
sudo iwconfig eth9 power off
sudo iwconfig eth9 commit
```

Replace "eth9" with the actual name of your wireless interface.

The third command may give an error as "feature not supported" that can be ignored.

Either one of the first two commands should work and will take effect immediately, _until_ your next reboot. 

So give the commands, then surf for an hour or two to check if it is effective. If it is effective, you can add the commands to your "/etc/rc.local" to take effect on every reboot.

Note that in the rc.local file, the last line should not be disturbed (ie, "exit 0")

Cheers prshah,
I will try your method very soon and report back with the results.

---

### Post by Rytron on 2008-07-05
Hi,

I presume I replace eth9 with wlan0?

Here is the output I got:

myusername@Xubuntu1:~$ sudo iwconfig wlan0 txpower fixed
myusername@Xubuntu1:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
myusername@Xubuntu1:~$ sudo iwconfig wlan0 commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device wlan0 ; Operation not supported.
myusername@Xubuntu1:~$ 

The internet connection only lasts for less than a minute and then drops.

:mad:

---

### Post by prshah on 2008-07-05
> **Rytron said:**
> 
myusername@Xubuntu1:~$ sudo iwconfig wlan0 txpower fixed
myusername@Xubuntu1:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
myusername@Xubuntu1:~$ sudo iwconfig wlan0 commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device wlan0 ; Operation not supported.
myusername@Xubuntu1:~$ 


Well the first command's worked. To confirm, give the ```
iwconfig
``` command, and you should get something similar to > ```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          [color=red]Power Management:off[/color]
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Note the line on power management. 

Since you say that it still doesn't maintain the connection, I guess the problem is elsewhere; sorry this didn't help out.

---

### Post by Rytron on 2008-07-06
Thanks for your effort anyway.
The search for the solution goes on...

---

