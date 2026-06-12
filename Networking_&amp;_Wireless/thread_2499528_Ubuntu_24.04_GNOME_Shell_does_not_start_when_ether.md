---
title: "Ubuntu 24.04: GNOME Shell does not start when ethernet is used"
date: 2024-07-30
forum: Networking &amp; Wireless
---

### Post by rakinar2 on 2024-07-30
I don't know what causes it, I disabled "quiet splash" in /etc/default/grub and ran `sudo update-grub`.
In the boot logs there wasn't anything special. Then I booted in recovery mode (without network), and it boots perfectly, gnome shell also starts up perfectly. 
Even if I normally boot it up, when ethernet is unplugged, it successfully starts gnome shell.

Then in recovery mode I tried to enable networking. In around 10 seconds everything became frozen. I was only able to use the sysrq-REISUB keys to reboot.
Same with normal boot. I booted up gnome shell again keeping the ethernet cable unplugged. Then after boot I plugged it in. And, it became frozen again.

This does not happen with Wi-Fi. I'm not sure what causes this as other linux distros (EndeavourOS on Hyprland) works perfectly with ethernet. Windows
also works fine with ethernet.

Also, after inspecting kernel logs, I see the following log:

```

rcu: INFO: rcu_preempt detected expedited stalls on CPUs/tasks: { 11-.... } 63119 jiffies s: 805 root: 0x800/.

```

The kernel log is filled with these logs. Then the gnome-shell process times out and crashes.
Here is the full syslog: [https://drive.google.com/file/d/15SaPX2y-MryjoLUyQyNlCPEIBoJYiGwb/view?usp=sharing](https://drive.google.com/file/d/15SaPX2y-MryjoLUyQyNlCPEIBoJYiGwb/view?usp=sharing)

Any help will be appreciated.

---

### Post by rakinar2 on 2024-07-30
Update: This seems to be fixed in kernel version 6.9.
The issue was probably: [https://github.com/torvalds/linux/commit/387f295cb2150ed164905b648d76dfcbd3621778](https://github.com/torvalds/linux/commit/387f295cb2150ed164905b648d76dfcbd3621778)

---

