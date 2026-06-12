---
title: "Network settings, static ip, wlan and wpa2"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by mkammerer on 2008-07-25
Hi,

I have a problem with the gnome gui to configure my wlan. I have a Dell Inspiron 1520 with an Intel 3945 ABG wlan chip. Laptop is running under Ubuntu 8.04. The WLAN is secured with WPA2 and has _NO_ dhcp server running. Now i want to use the Gnome GUI and its feature to have different profiles (i need a profile for at home, static ip and a profile for my university, dhcp). So i open that GUI, select properties of the wlan connection, enter the ESSID (only numbers and a dash -, does that cause problems?), set the security to WPA2 and enter the password. Now I do the ip configuration. Click OK, but nothing happens. I just can't ping my router (192.168.1.1, my IP is 192.168.1.18/24). If i open the settings for the wireless card again, the security is resetted to WPA and the password field is blank.
How to get this thing working with usable network profiles?

Thanks,

M. Kammerer

---

### Post by KenF on 2008-07-27
I'm on 7.10 (gutsy), but I also have had problems setting up networking with static IP's.  I've found that after I've set it up (using System->Administration->Network):
[LIST=1]
[*]It doesn't work immediately.
[*]The wired network works on reboot and subsequent reboots [is this windows?]
[*]The wireless networking with the static IP does not work initially or on reboot.  However, if I issue a "sudo /etc/init.d/networking restart" both the wireless and wired networking works immediately, but the wireless does not work on reboot.
[/LIST]

I suspect that for the third point (wireless with static IP), I should probably just add that to /etc/rc.local (before the exit 0; and chmod +x it) to make sure it always works.

Kind of a pain ... and I hope this helps you.

KenF

---

