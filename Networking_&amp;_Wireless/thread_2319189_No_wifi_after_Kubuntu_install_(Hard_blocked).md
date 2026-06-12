---
title: "No wifi after Kubuntu install (Hard blocked)"
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by madcoder2 on 2016-04-01
Hello, I've been battling with this problem for the past 2 days. I installed Kubuntu and I can't connect to any wireless network.
When I run "rfkill list" command, the following appears:

0: phy0: Wireless LAN
           Soft blocked: no
           Hard blocked: yes

I already tried lots of solutions found in different posts around this forum, lots of commands and none solved this problem. I also tried updating the firmware and nothing changes.
The laptop is an HP Pavilion 13 x360. There is no wifi switch, the only switch in the keyboard is the "airplane mode" one. Pressing that does nothing.
There is an option in the bios that has something to do with enabling network adapter during boot; that is enabled. 
Already tried reinstalling Kubuntu... problems persist.

I don't know what else to do to solve this.

---

### Post by jeremy31 on 2016-04-01
Post ```
lsmod | grep acer
``` results

---

### Post by madcoder2 on 2016-04-01
Nothing. Does it have anything to do with the laptop's brand?

---

### Post by jeremy31 on 2016-04-01
Many times we see this issue with HP laptops with acer-wmi module loaded

Some times it can be fixed by shutting off the laptop and removing the battery, possibly a BIOS reset to defaults

---

### Post by madcoder2 on 2016-04-01
I tried blacklisting the wmi module and resetting the bios to defaults, but the problem is still there.
The battery is integrated, I can't remove it.

---

### Post by madcoder2 on 2016-04-06
bump

---

