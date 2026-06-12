---
title: "Wireless works, then doesn't in 7.10"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by skoalman88 on 2007-10-26
I am using an Edimax 7318USG and it worked for about 5 minutes and then stopped with network-manager, then I installed WICD and it worked again for 5 minutes and then stopped.

If I use sudo ifconfig wlan0 down iwconfig does not show any change. When I try sudo ifconfig wlan0 up, i get this error: "SIOCSIFFLAGS: Input/Output error"

Any thoughts

---

### Post by Lambert on 2007-10-27
Look in your syslog file for any output relating to your wireless. 

Going through the menus to adminstation you will see syslog. Open that and look through there.

---

### Post by skoalman88 on 2007-10-28
Anything in particular I should be looking for?

---

### Post by LeventO on 2007-12-22
I'm having the same problem as this user. My wireless keeps cutting out.
sudo ifconfig wlan0 up gives me "SIOCSIFFLAGS: Input/Output error"
I pull out the card (it's USB) and put it back in and it works again (sometimes for just 30 seconds, sometimes a couple of minutes and sometimes it leaves me alone for the rest of the day).

I'm on the AMD64 version of Gutsy (7.10), and I have a Cnet CWD-854 wireless card [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCnet](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCnet)
it's not on the supported cards list but I think it's just the USB version of the CWP-854.
It originally worked straight out of the box when I installed Feisty, and since upgrading to gutsy it's been giving me grief.

just after i had pulled it out and put it back in the syslog messages looked like this:
Dec 23 16:36:43 levent-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Dec 23 16:36:43 levent-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Dec 23 16:36:43 levent-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers

and the kern.log is attached.

any help would be appreciated.
let me know any other data I can provide to help get my problem diagnosed.

kind regards,
Levent.

---

### Post by LeventO on 2007-12-26
I just tried to use a different wireless card, and it also has the same problems so it doesn't appear to be a problem with the card. maybe there is something wrong with my USB drivers?

---

