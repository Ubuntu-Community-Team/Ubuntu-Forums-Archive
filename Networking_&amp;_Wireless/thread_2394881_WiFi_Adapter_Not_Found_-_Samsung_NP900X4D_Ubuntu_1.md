---
title: "WiFi Adapter Not Found - Samsung NP900X4D Ubuntu 18.04 LTS"
date: 2018-06-23
forum: Networking &amp; Wireless
---

### Post by falsestar on 2018-06-23
Hi All,

I recently installed Ubuntu 18.04LTS on my laptop and the WiFi Adapter is not working (i.e. says no WiFi adapter found on the WiFI Settings) 

Could anyone help me on how to get this fixed? 

Here's the adapter details: 
[COLOR=#363636][FONT=SamsungOneLatinWeb]802.11 a/b/g/n, 
802.11 a/b/g/n, 
Intel Centrino Advanced-N 6235, 
2x2, Intel Centrino Advanced-N 6235, 2x2, 
802.11 a/b/g/n

Here's the laptop that I have: [/FONT][/COLOR]https://www.samsung.com/us/business/support/owners/product/series-9-ultrabook-np900x4d/


[COLOR=#363636][FONT=SamsungOneLatinWeb]


[/FONT][/COLOR]

---

### Post by pete-br on 2018-06-23
Open a terminal windows and issue the command dmesg.
It should show a long list of messages related to your hardware.
Especially look for any lines shown in red.

---

### Post by jeremy31 on 2018-06-23
Moved to Networking and Wireless

---

### Post by praseodym on 2018-06-24
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by falsestar on 2018-08-25
Sorry guys, work has been crazy so I haven't responded to this thread. 

@[COLOR=#DD4814][COLOR=#000000][pete-br]("https://ubuntuforums.org/member.php?u=2065489") I'll let you know what results come in[/COLOR][/COLOR]

---

### Post by falsestar on 2018-08-26
hey @pete-br and @praseodym - I think I ended up solving the issue. I reinstalled 18.04 whilst having wired ethernet and it just worked out of the box this time. Currently connected via WiFi and typing this out :) 

Thanks for the quick response guys - and sincere apologies for not getting back on this earlier.

---

