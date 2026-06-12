---
title: "100% CPU on dual processor?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by PA-J3Cub on 2008-12-05
Hello everyone. I've just installed Ubuntu 8.10 on a HP G60-127NR 2.0GHz dual processor laptop with 3GB ram, dual-boot with Win Vista.

No problems during the install.

However, Ubuntu is running extremely slow. While viewing a website in Firefox I held the down arrow too long and it too approx 3 minutes for it to stop scrolling.

System monitor shows processor #1 is at 0.0% while processor #2 is at 100.0%. In looking at the Processes page, only gnome-system-monitor is displayed with 0% CPU activity. If I move my mouse XORG process is displayed with a CPU % of anywhere from 2% to 64%.

I've searched other posts on the forums but none of them have pointed me in the right direction. I've seen posts discussing issues with wireless services to issues after upgrades to issues with applications. However, this is a fresh install with no applications, services added.

Anyone have any suggestions?

TIA

---

### Post by stinger30au on 2008-12-05
get rid of firefox and use opera. i had the same dramas

---

### Post by PA-J3Cub on 2008-12-05
Firefox isn't running. I just used the web thing as an example of how slow everything is running. I've rebooted and everything is slow. If I boot into Vista everything runs fine. (I hate typing that).

I'm sure there is a resolution here. I will continue to work on it. I just thought I'd post the issue here in case someone has experienced this as well.

---

### Post by PA-J3Cub on 2008-12-05
OK, well, the issue is resolved. I updated the accelerated graphics driver and the system performance and speed is 1000% better. Things are running smooth and fast.

However, with System Monitor up I still see somewhat high processor utilization. I'm still seeing utilization of 40 - 60%. However, I've seen other threads that discuss this and some replies say this is normal. I see no reason for it, but, I'm glad the performance issue has been resolved.

---

