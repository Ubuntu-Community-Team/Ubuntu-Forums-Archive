---
title: "wireless is not working on 10.10"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by bl42ed0 on 2011-04-04
i have an hp m9350f and i installed ubuntu 10.10 on it and the wireless isnt working. i tried sudo ifconfig wlan0 up as well as sudo rfkill unblock all to no avail. any help on this specific NIC card?? thanks.

here is some info:

m9350f:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

m9350f:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

everything is 'true' in the networkmanager.state file as well

---

### Post by SuaSwe on 2011-04-04
Hello!

Could you clarify what it is that isn't working? How far into the process of setting up a wireless network do you get before it fails?

---

### Post by bl42ed0 on 2011-04-05
sorry, it worked when i updated everything. thanks though!

---

