---
title: "Wireless wont work in 10.04!"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Userkan232 on 2010-05-12
I just did a fresh install of the latest version of ubuntu, and I cant connect to my wireless network. Whenever i go to manage network, and click wireless, none show up and I am 2 feet away from the router. They show up on my windows computer, so I dont know why thy wont here. 
A lot of other posts ask for this info, so here:

iwconfig: lo        no wireless extensions.

eth0      no wireless extensions.

[noparse]eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/noparse]


I have the Intel PRO/Wireless 2915ABG [Calexico2] Network Connection 

Please help

---

### Post by Userkan232 on 2010-05-12
anyooone?

---

### Post by earthpigg on 2010-05-12
edit: nevermind, i have no idea :(

it is listed as working OOB here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

but that entry hasn't been updated since 10.04 came out.

do you have ipw2200 installed? search in synaptic.

---

### Post by pizza-is-good on 2010-05-12
I had to install the driver for my wireless card before it worked.
System>>Administration>>Hardware Drivers
For my Dell it is 'Broadcom STA wireless driver'

~pizza

---

### Post by mbyrd11 on 2010-05-12
yup i had the same problem when i did a fresh install. i remember that i was soo frustrated haha

---

