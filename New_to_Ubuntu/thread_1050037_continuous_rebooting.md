---
title: "continuous rebooting"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Buccaneer on 2009-01-25
Hi everyone,

I'm a new user of ubuntu and it's a really good experience so far. There's only one thing nagging me. It keeps rebooting for no reason. I have my power settings on never sleep, no screensaver. but when I don't use it for about a half hour, it will reboot. This is really annoying when i'm downloading from torrents. Can anyone help me?

Greetings,

Max

---

### Post by Rim on 2009-01-25
<.< umm continuous rebooting like that can mean one or 2 things imo. Either your PSU (Poer Suply Unit - where u plug in ur pc) is malfunctioning either because the motherboard connector is oxidising and getting buned in th process misfireing ^^; in this case change either the cables if u can or the whole PSU unit.

<.< or theres an auto shut-down set or something i dun get yet because i'm new to Ubuntu :P.

Constant reboot issues usually end up being the PSU at fault.

---

### Post by Buccaneer on 2009-01-25
But if it would be that it should have been rebooting under windows to right? And I have a laptop so I can't really screw around inside.

---

### Post by KIAaze on 2009-01-26
It could be because of overheating (altough when that happened to me, it just shut down instead of rebooting).

Check your logs to see if that's the case. I don't know exactly where those things are logged, but it's probably in /var/log or in the "kernel ring buffer" (use "dmesg" to read it.)

Here's more info about overheatring issues:
[http://www.linuxquestions.org/questions/linux-kernel-70/deactivating-forced-shutdown-because-of-high-temperature-446452/](http://www.linuxquestions.org/questions/linux-kernel-70/deactivating-forced-shutdown-because-of-high-temperature-446452/)
(cf links given at the end of the thread)

In my case, the solution was to open up and clean my laptop. (sudden shutdowns happened in windows too)

---

