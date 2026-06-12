---
title: "wlan, iwl3945, periodic wlan-logoff/login, freezing"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by maxclaus on 2008-09-03
Hi all,

i'm using Ubuntu 8.04 since 6 weeks and still have some problems to solve. After consulting some other forums for a while and sadly no usable result, i thought to try it in Your forum again.

The system:
- laptop Acer Extensa 7620
- with Ubuntu 8.04, Kernel 2.6.24-19-generic
- wlan adapter Intel Pro/Wireless 3945ABG
- wlan driver iwl3945
- linux-backports-modules-2.6.24-19-generic additionally loaded for wlan LED function
- internet: DSL
- wlan router: AVM Fritzbox wlan3170 with the latest available firmware, currently in WEP mode

Correct functions:
- roaming mode works, available networks are shown in the applet of NetworkManager, immediate login with 'myrouter', mode WEP 
- no connection problems as long as there is data transfer to the router

Malfunctions:
- laptop <=> router connection idling (no data transfer): automatic logoff/login every 20 minutes with a break of appr. 1/10 sec duration generating 2 according entries in the routers eventlog => means 30 entries in 10 hours and eventlog filled with trash. The breaks can also be seen in the terminal with 'iwevent'
- the automatic login (roaming) sometimes failes => roaming freezes
- activation only works either by booting again or with the commands 'sudo rmmod iwl3945 + sudo modprobe iwl3945'
- the hardware wlan button is not working correctly: disabling yes (LED => off), enabling not possible => no severe failure more probaby 'nice to have...'

Current status:
-currently roaming is disabled to avoid 'freezing', the wlan connection is realized with the following additional entries in /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
  wireless-mode Managed
  wireless-essid <myrouter>
  wireless-key <hexWEPKEY128Bit>

-Connection is working stable (no roaming => no freezing, the router must be activated and running stable before booting the laptop), but the measure does not eliminate the 20 min periodic wlan-logoffs/logins with the according entries in the routerlog (20 min after last data transfer the first logoff occurs)

Remark: Windows XP on the same computer (dual boot system) is working correctly, no logoffs /logins during idling of the wlan connection. 

Does anybody have an idea where these 20min interrupts could come from and how to avoid? Thanks in advance / maxclaus

---

