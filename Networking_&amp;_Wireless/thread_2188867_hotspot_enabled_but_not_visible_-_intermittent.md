---
title: "hotspot enabled but not visible - intermittent"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by monoclemike on 2013-11-19
I am running Version 12.04 LTS with a Belkin G Plus MIMO USB wireless adapter. lsusb command says it is badged Ralink RT2573.

I have created a hotspot using Network Manager and it appears to have started correctly. The problem is that the machine name is only very intermittently available to other machines. 95% of the time it does not appear and it disappears before I can log in.

Has anyone got this working?

Some diagnostics:
mike@mikelap:sudo iwlist scan | egrep -i 'chan|ssid'
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    ESSID:"mikelap"
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    ESSID:"ALICE_MICHAEL_WZ"
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    ESSID:"ALICE_MICHAEL_WZ"

The other wireless adapter is on-board and faulty but there is no switch on the laptop to disable it.
 ** I have just disabled it in blacklist.conf and the problem is still there! **

The USB adapter works very well when used to access my ADSL modem.

I have 4 other devices that I use to test if it has become visible namely iPod, Android tablet, Chromebook, NowTV bx.

---

