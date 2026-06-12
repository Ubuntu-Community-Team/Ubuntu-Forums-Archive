---
title: "Wifi only works satisfying when MBP running on battery"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by Thallid on 2014-09-30
Hello!

I have a Macbook Pro 13" Retina 11,3 running Trusty Tahr. When I plug in the AC/DC-adapter the wireless becomes horrendously slow. I get about 2-3 Mbit/s, it goes up and down, and it feels really unresponsive/laggy. When I unplug the adaptor, the wireless network seems to work fine with a bandwidth between 60-70 Mbit/s.

In my world it should be the other way around, but it isn't.

I've tried: Upgrading to latest mainline kernel, installing drivers from Utopic (6.30.223.248), I've turned off power management in powertop but then it acts like it's running on AC-power again.

What shall I do? MBP has a great battery life but ofcourse it can't run forever.

```
$ uname -r
3.16.3-031603-generic
```

```
$ lspci -v | grep Wireless
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
```

Can you lure the wireless adapter to go into a power saving mode maybe?

I appreciate any help I can get

---

### Post by tgalati4 on 2014-09-30
It could be noise being injected into the computer from the power supply.  Do you get a hum from your earbuds if you plug in the power supply?  If so, then the power supply might have a defect.  Try another.  Try plugging into different outlets around the house.  It's possible that you have a high-frequency noise source on your lines.  Do you or your neighbors have a powerline ethernet extender plugged in?  Try unplugging wireless handsets in the house.

Set the power management settings to maximum performance for both AC and battery.  Note any wireless network differences.  Then set power management to powersave for both AC and battery, then perform your testing again.  Post any differences.

Clean the contacts on your magsafe connector with a toothpick.  Rub the gold spots on both the computer and the power adapter.

Look in your log files.  Open a terminal:

```
more /var/log/syslog
```

Here's another possibility--a bad battery.  Shut down, pull the battery out.  Plug in AC and boot off of AC only.  Test your wireless speeds.  If you get normal speeds, then you might suspect that the battery has a subtle fault.  My theory is that the battery is drawing too much current (even though it works) and that puts the wireless card into a power-saving mode--which will generally lower network throughput.

---

### Post by Thallid on 2014-10-01
> **tgalati4 said:**
> It could be noise being injected into the computer from the power supply.  Do you get a hum from your earbuds if you plug in the power supply?  If so, then the power supply might have a defect.  Try another.  Try plugging into different outlets around the house.  It's possible that you have a high-frequency noise source on your lines.  Do you or your neighbors have a powerline ethernet extender plugged in?  Try unplugging wireless handsets in the house.

Set the power management settings to maximum performance for both AC and battery.  Note any wireless network differences.  Then set power management to powersave for both AC and battery, then perform your testing again.  Post any differences.

Clean the contacts on your magsafe connector with a toothpick.  Rub the gold spots on both the computer and the power adapter.I only got one power supply for my Mac and I live in a small appartment so I can't really move it around. But since it's running fine in OS X, can it still be a hardware problem? 

Yesterday it got troublesome even with the power unplugged. Maybe I've done something to the system that I shouldn't have, who knows... I was completely sure that it got slower when I plugged in the power supply but now I'm not so sure any more. :S I just want it to work because when it does the Macbook Retina + Ubuntu is an awesome combination!

> **tgalati4 said:**
> Look in your log files.  Open a terminal:

```
more /var/log/syslog
```

Here's another possibility--a bad battery.  Shut down, pull the battery out.  Plug in AC and boot off of AC only.  Test your wireless speeds.  If you get normal speeds, then you might suspect that the battery has a subtle fault.  My theory is that the battery is drawing too much current (even though it works) and that puts the wireless card into a power-saving mode--which will generally lower network throughput.
I'll try that and see what happens!

The log file is clogged with entries from something with the power management for the SSD-drive. It gets 100 MB bigger every day. I did some research on this and it gets a lot better with power management sett to "medium_power" but not perfect. I've browsed through it a couple of times and I cant see anything that has to do with the wireless. :(

I'm going to try to remove the battery and see what happens!

---

