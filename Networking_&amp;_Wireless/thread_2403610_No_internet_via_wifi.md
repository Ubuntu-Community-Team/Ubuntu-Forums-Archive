---
title: "No internet via wifi"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by Coto_Paxi on 2018-10-13
The network manager shows that the computer (Lenovo Edge E325) is connected to wifi, but I have no internet access, I can only access the internet via cable.

The command "nmcli device" gave the following output:

> 
[FONT=monospace][COLOR=#54FF54]**skippy@skippy-ThinkPad-Edge-E325**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ nmcli device  [/COLOR]
DEVICE    TYPE      STATE       CONNECTION          
[COLOR=#18B218]enp2s0    [/COLOR][COLOR=#18B218]ethernet  [/COLOR][COLOR=#18B218]connected   [/COLOR][COLOR=#18B218]Wired connection 1[/COLOR]
[COLOR=#18B218]wlp1s0b1  [/COLOR][COLOR=#18B218]wifi      [/COLOR][COLOR=#18B218]connected   [/COLOR][COLOR=#18B218]MiFibra-EEE4[/COLOR]
[COLOR=#000000]lo[/COLOR][COLOR=#000000]loopback [/COLOR][COLOR=#000000]unmanaged[/COLOR][COLOR=#000000]--[/COLOR]
[COLOR=#54FF54]**skippy@skippy-ThinkPad-Edge-E325**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT] 

Again, the laptop seems to be connected to wifi, but I have no Internet access.

Thanks for your help!

---

### Post by Coto_Paxi on 2018-10-13
Solved! My 15 year old sun is the system administrator of our wifi and he has disabled me! When I opened Firefox I got the message from our router that my access is denied! I got this message ONLY in Firefox, Opera and Falkon did not display it.

Sorry for this thread!

---

