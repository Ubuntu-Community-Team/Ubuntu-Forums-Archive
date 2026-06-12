---
title: "No wireless connection after resume rtl8192se driver"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by hkskoglund on 2014-03-14
Hi, i have a problem with proper suspend of my laptop (13.10/linux 3.11.0.18-generic). It works ok, if I manually type sudo pm-suspend, but fails if I use the ubuntu gui Suspend option. I ran a diff on the **/var/log/pm-suspend.log** and found that suspend via gui gives an error message;

    'failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory'. On the next line i get

'/usr/lib/pm-utils/sleep.d/60wpa_supplicant suspend suspend: success' ??

In this case I must use; **nmcli nm sleep false **to wake up the wireless card again

In the log from command-line activation I get;
    
    Running hook /usr/lib/pm-utils/sleep.d/60wpa_supplicant suspend suspend:
    Selected interface 'wlan0'
    OK
    /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Is this the cause of failed resume? What can be done to resolve this?

---
P.S Also sent a question to [http://askubuntu.com/questions/433734/suspend-takes-very-long-time-wireless-card-unavailable-in-network-manager-on-re](http://askubuntu.com/questions/433734/suspend-takes-very-long-time-wireless-card-unavailable-in-network-manager-on-re)

---

