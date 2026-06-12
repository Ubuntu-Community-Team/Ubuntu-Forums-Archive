---
title: "ubuntu 14 wifi intermittent"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by brandonabandon on 2014-11-08
hello ubuntu community, 

           as i was unable to find specifically the solution and in hopes of an fyi thread, i will update tommorrow details regarding this problem.

1. steps to reproduce:
[LIST]
[*]fresh install of 12.04 precise 
[*]system upgrade to 14.04 trusty 
[*]fresh install vmware VMware Workstation 10.0.2 build-1744117 
[*]fresh install vm windows 7 32 bit 
[/LIST]

2. steps ive took to resolve:
[LIST]
[*]setting wifi router as follows-wpa2,channel 11,disable mode n 
[*]adding country code-from 00 (default) to US 
[/LIST]
sudo iw reg set US


[LIST]
[*]ignore ip6v, set mode- 
[/LIST]
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf 


[LIST]
[*][FONT=arial]reboot[/FONT]

[FONT=arial]to be accurate, the problem did not occure until installing the virtual machine.i dl large amounts of code via repositories beforehand (trusty) no problem. upon installing the vm the problem begins.

system specs; Dell optiplex 755, ubuntu 14.04, 64bit, netgear wireless adapter

[http://pastebin.com/P05GEAur](http://pastebin.com/P05GEAur) <--wireless script, as mentioned--->[http://ubuntuforums.org/showthread.php?t=2243493](http://ubuntuforums.org/showthread.php?t=2243493)[/FONT][FONT=arial]
[/FONT][FONT=arial]i believe the fixes i have applied[/FONT][FONT=arial] will fix this problem and i will mark as solved if so.[/FONT] 
[/LIST]

---

### Post by chili555 on 2014-11-08
This thread may be helpful: [http://ubuntuforums.org/showthread.php?t=2248151&page=2](http://ubuntuforums.org/showthread.php?t=2248151&page=2) See my post #15 and also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809/comments/6)> I would certainly try the patched kernel as mentioned in the bug report You have the tell-tale symptom:> fail to flush all tx fifo queues

---

### Post by brandonabandon on 2014-11-08
id rather not install a new kernel as ive read it could negatively affect the vm i spent hours on configuring. i will if necessary. the log of wifi dropping completely is strange, seems connection is solid for a few hours initially after a reboot. once the problem occurs, the connection was dropping, then reconnecting 5-30mins intervals, occasionally dropping, and unable to reconnect unless rebooting. this was before the fixes ive applied recently. i rebooted my pc minutes ago, so far so good, i will reply with results either when/if connection fails or tommorrow if/when connection is consistent. thanks

---

### Post by brandonabandon on 2014-11-08
the above changes are not affecting internet speed.

edit: internet speed has improved immensely. a dl 100mb @ 45min. to 10min...and to think i figured my service was @ fault. i think vmnet was the culprit, as my vm wifi config is bridged.

---

### Post by brandonabandon on 2014-11-09
my wifi is fixed now. also netflix no longer loading screen during "high traffic" (multiple dl'ing, ul'ing, etc.)

---

