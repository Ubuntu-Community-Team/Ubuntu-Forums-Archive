---
title: "Can't control bluetooth in saucy"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by mike.doherty on 2014-02-21
AskUbuntu yielded no fruit: [http://askubuntu.com/questions/423668/cant-control-bluetooth-in-saucy](http://askubuntu.com/questions/423668/cant-control-bluetooth-in-saucy)

I can't get bluetooth on my laptop to work properly in Ubuntu 13.10.

[list]
[*]There is no bluetooth indicator visible, but indicator-bluetooth is installed
[*]The bluetooth control panel is greyed out, with the "power switch" for bluetooth in the "off" position. When I change it to "on" nothing happens. There is nothing in syslog.
[*]service bluetooth status reports that the service is running
[*]hcitool dev lists hci0
[*]hciconfig shows that hci0 is "UP RUNNING"
[*]hcitool scan lists bluetooth devices when they're visible
[/list]

lsmod shows two bluetooth modules:
```
$ lsmod | grep blue
bluetooth             372041  12 bnep,btusb,rfcomm
toshiba_bluetooth      12852  0 
```

So, it looks like the hardware is detected, powered, and working. But none of the graphical utilities to control bluetooth are. What do I need to do so the normal bluetooth software works properly?

---

### Post by mike.doherty on 2014-02-22
I've found that removing then re-adding the btusb kernel module, then using rfkill unblock bluetooth will bring Bluetooth up. This causes the Bluetooth section of the control panel to start working again, as well as indicator-bluetooth to appear.

If I turn off Bluetooth with either of these, indicator-bluetooth disappears, and neither will work to turn Bluetooth back on again.

This obviously isn't ideal, but it's sufficient to get my devices communicating.

---

