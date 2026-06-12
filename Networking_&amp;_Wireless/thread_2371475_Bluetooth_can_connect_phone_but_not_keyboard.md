---
title: "Bluetooth can connect phone but not keyboard"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by &amp;*@Fth&amp;% on 2017-09-14
I've seen several posts about this error message on various forums (so surprise, it's so descriptive), but none of the solutions have worked for me. I'm running Kubuntu 17.04 with bluez 5.43. I can connect to my phone, but not to my keyboard. I used to be able to connect to my keyboard just fine, but after upgrading to Ryzen I can't.

```
$ bluetoothctl
[NEW] Controller <addr> <pc name> [default]
[NEW] Device <addr> Keyboard
[NEW] Device <addr> Phone
# power on
Changing power on succeeded
# scan on
Discovery started
[CHG] Controller <addr> Discovering: yes
# agent on
Agent registered
# default-agent
Default agent request successful
# connect <phone addr>
Attempting to connect to <phone addr>
[CHG] Device <phone addr> Connected: yes
# connect <keyboard addr>
Attempting to connect to <keyboard addr>
[CHG] Device <keyboard addr> Connected: yes
Failed to connect: org.bluez.Error.Failed
[CHG] Device <keyboard addr> Connected: no
```

---

