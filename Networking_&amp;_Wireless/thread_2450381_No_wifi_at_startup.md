---
title: "No wifi at startup"
date: 2020-09-12
forum: Networking &amp; Wireless
---

### Post by pla-jager on 2020-09-12
Build:
[LIST]
[*]CPU: Ryzen 3800x
[*]Graphic: RTX 2070 super
[*]RAM: 16 GB @ 3200mHz
[*]Motherboard: Asus TUF b550m WI-FI
[*]Network: Intel AX200 (Built-in)
[*]OS:
[LIST]
[*]Ubuntu 20.04.1 LTS (on host-machine)
[*]Windows 10 (on host-machine)
[*]Seperate bootloader
[/LIST]
[/LIST]
Problem: 
Ubuntu cannot use Wi-Fi at startup sometimes, not always. There is no wifi icon on the top corner. I go to setting there is no WiFi tab either. Restart does not fix the problem. 
However, if I restart to Windows, then restart again to Ubuntu, the wifi is back, this always work. If sometime I first start my computer to windows, then restart to Ubuntu, the wifi always works.
My WiFi in windows always works.
It appears that restarting to ubuntu from windows is a necessary measure to ensure WiFi functional in Ubuntu. 

Base on the given information, any clue on what is causing the problem?

---

### Post by TheFu on 2020-09-12
What is "startup?"

A VM doesn't use wifi. It uses a fake network adapter, which should be virtio (for all non-Windows systems) or Intel/PRO 1000, if Windows.  A VM only sees fake hardware. Even the GPU is fake.

Some important terms - on Unix-like systems, including Ubuntu, there are a few different things that can be confused as "startup."
[LIST]
[*] boot, 
[*] before login, but after boot
[*] after login
[/LIST]

There are different capabilities for all of these things, depending on the systems settings.

If you set networking settings to be for 1 user (per-userid), then those won't be enacted until AFTER login. No networking will exist prior to that point.

If you set networking settings to be for all users, then the network settings are controlled at the system level and require sudo/root to modify. This can be a hassle, but it means we can access through network protocols like cifs, nfs, ssh, and others, without actually logging into the system locally.

Hope that has helped.  If you can, please clarify when you expect networking to be available, assuming it isn't just a bad setting in the VM configuration of vbox.

---

