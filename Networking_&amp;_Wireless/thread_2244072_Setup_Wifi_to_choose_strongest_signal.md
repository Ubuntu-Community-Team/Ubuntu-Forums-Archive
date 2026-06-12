---
title: "Setup Wifi to choose strongest signal"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by goethesf on 2014-09-13
Hi ...

My research before posting found this [unresolved thread]("http://ubuntuforums.org/showthread.php?t=1847384&highlight=wifi+choosing+strong+signal").

I live in an old house with thick walls and I have multiple Wifi routers to provide whole house coverage. I'm using different SSID/passwords as having everything the same wasn't working for for me. I'd like to configure Ubuntu to choose the SSID with the strongest signal and auto-connect to that network. 

Any suggestions?

Thanks in advance,
-g

---

### Post by ian-weisser on 2014-09-15
That behavior cannot configured. There is no setting for it.
However, that behavior can be programmed. The tools to monitor network SSIDs and strengths and tell Network Manager (NM) to change networks can be programmed in any convenient language of your choice.

Network Manager includes a command-line interface (nmcli). See the manpage (man nmcli) for the options. Handy for scripting.

Network Manager also interacts with dbus. See the d-feet application (provided by the d-feet package) for a good introspection tool to explore NM's dbus interface. Handy for programming languages with dbus modules.

---

