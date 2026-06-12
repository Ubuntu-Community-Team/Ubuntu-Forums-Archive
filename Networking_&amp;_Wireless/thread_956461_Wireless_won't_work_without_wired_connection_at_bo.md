---
title: "Wireless won't work without wired connection at boot-up"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by mbratch on 2008-10-23
I am using a wireless USB device based upon the RTL8187B chip.
I am using the Windows driver and ndiswrapper.

To get it to work at all, I had to put a script in /etc/network/if-pre-up.d that looks like this:

```

/sbin/iwconfig wlan0 essid <My_Access_Point>
/sbin/iwconfig wlan0 key <My_WEP_Code> open
/sbin/iwconfig wlan0 channel <My_Channel>
/sbin/iwconfig wlan0 mode Managed

```

The system ignores settings in the "interfaces" file, but seems to do the scripts under /etc/network OK.

But the oddest thing is happening. Although I have the eth0 (wired LAN) set up for manual configuration (not auto-loading), it must be plugged in or the computer won't boot with networking working.

In other words, if I reboot the PC, wireless networking will not work at all if the wired network cable isn't connected. iwconfig, ifconfig, and iwlist all show output that looks normal. But I can't ping anything on the network, nor the access point/router itself. If I just connect up the network cable and reboot, the wireless comes up on its own and all works fine (and the output of these tools looks the same as in the non-working case). And like I said, the wired network isn't ON in this case, the cable just has to be connected for the wireless to come up. Once up, I can disconnect the cable and the wireless works fine until the next reboot.

Can someone give me a hint as to what the heck is going on?

Thanks. :confused:

---

### Post by mbratch on 2008-10-23
boink

---

### Post by mbratch on 2008-10-27
After buying this wireless USB adaptor that claimed Linux compatibility and fussing with this thing for awhile, I am giving up on wireless and Ubuntu for now. It does not appear ready for prime time, and nobody seems to understand how it works. I see scores of problems being posted on this forum.

---

