---
title: "nmcli device status command does not work on 18.04.1 LTs"
date: 2018-11-28
forum: Networking &amp; Wireless
---

### Post by cam17 on 2018-11-28
When I enter the command "nmcli wlp1s0 status" I get the message "error: argument 'wlp1s0' not understood. try passing --help instead.  If I perform a ifconfig I get the the list of interfaces1 of which is wlp1s0 with a IP address, netmask and broacast address.  I bring this up because somewhere on the forum I was told that ifconfig is no longer being used and was replaced by the command ip but suddenly my Ubnutn 18.04.1 as of Nov-28-2018 is responding to the command "ifconfig"   If I want the status of my WIFI interface what command should be used? Can anyone tell me why the above is not working?  Thx

---

### Post by mitesh.agrwl on 2018-11-28
correct command is 

```
$ nmcli device status <INTERFACE-NAME>
```

---

### Post by cam17 on 2018-11-29
thanks

---

