---
title: "Automatic Wireless"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by milanvora2 on 2008-08-17
I have a WNDA3100.
I installed ndis ... configured network and all works well.
However everytime i reboot, the wireless doesn't start automatically 
(the usb stick keeps blinking). If i go again on network and notice that the password is either longer than the one i entered or the setting is on 
wpa instead of wpa2.

Ayn way i can automate this so that i don't have to do this each time
Thanks for your help

---

### Post by milanvora2 on 2008-08-17
In case my above post was not sufficient explicit.

1) I got a WND3100 usb network adapter
2) I installed ndiswrapper-utils, ndiswrapper-common  and ndisgtk
3) Using ndisgtk, i installed the supplied driver with my adapter.
4) I went under System > Administration > Network
  chose to disable roaming mode
  Chose essid, entered encryption type & password, automatic dhcp
5) Now the wireless works.

- If I reboot system, the wireless adapter keeps on blinking
- so i have to manually re-do step 4
  I notice that the encryption has changed. I also notice the password dots
  are longer.
- I have to re-enter setting as it works

- What am I doing wrong ? 
- Why can't i see all unavailable networks under network manager ?

---

### Post by pytheas22 on 2008-08-17
First of all, run these commands to make sure that ndiswrapper is getting loaded at each boot:
```

sudo -s
echo 'ndiswrapper' >> /etc/modules
```

Please also try turning off roaming mode--it should not be necessary.  Are you unable to connect in roaming mode for some reason, and if so, why?

You could also try using [wicd]("http://wicd.sourceforge.net") to see if it works better than Network Manager (what you're currently using); it does for most people.

---

