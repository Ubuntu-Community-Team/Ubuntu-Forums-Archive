---
title: "Strange behavior after install, ioerrors."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Mjölner on 2009-02-03
Hi. Thanks for the help in advance.

After moving house ( I live in a houseshare with no access to the wireless router or cabled lan) , I was suddenly not able to get a network connection. But I did have one though, so I new it was working, and it's working now and has been for all others in the house the whole time. 

So without access to the internet and online help, I reinstalled hoping that this would cure my wireless ills. It did! and I am now writing this. My problems now however are of a different nature.

I have had to attempt install many times and failed and I get mostly IO errors(8.04 and 8.10), and when I have had success as soon as I try to update, restart, install graphics drivers or do similar things, and reboot, the OS won't load correctly or hangs. I have tried ZenWalk and had no problems installing or running the OS, but with my level of knowledge wasn't able to configure the wireless.

My question is this. How do I go about getting logs or info from the system and understanding from this info what I can do? I am hoping that you can help me to do this and understand what the problems are. 

I am a noob, but not scared of the terminal :)

---

### Post by petervk on 2009-02-04
Great list of the log files ubuntu uses:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

May be something in the /var/log/syslog file.

---

### Post by Mjölner on 2009-02-06
Thanks for the input:)

I will defiantly look into that!

I think I found my problem though....
I have a PATA and SATA drive and when looking at the textual recovery boot, I found that the PATA drive ( my slave/backup drive) was having problems with interrupt requests, so... I fiddled around with the jumpers on the drive and the cable positioning.

The solution was to have the drive let the cable positioning relay its priority. ie; jumpers set to cable select and the drive plugged into the middle connector so the drive gets told it's the slave by the ?.

If you could leave a link that helps me understand this I would be grateful.
:D

---

