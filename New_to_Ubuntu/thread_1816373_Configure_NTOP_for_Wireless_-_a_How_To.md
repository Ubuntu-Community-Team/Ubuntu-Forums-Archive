---
title: "Configure NTOP for Wireless - a How To"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-08-01
I wanted to use ntop to monitor my broadband usage as my ISP (AT&T - dsl) has capped monthly usage at 50 gig.

I installed ntop and surfed to localhost:3000 but ntop reported that 'eth0' was the device being monitored. I don't have ethernet access (eth0 or ethernet device 0) and posted at this Abs. Beginner's forum:

[Re: How to? config NTOP with wireless wlan0?]("http://ubuntuforums.org/showthread.php?t=1809374")

how do I configure it? After a week and and 32 viewings, and no response, I found another [post]("http://ubuntuforums.org/showthread.php?t=480035") from August 2007 about ntop and wireless. It suggested changing the config file from eth0 to eth1. I tried that, but it did not work. Then I took a big chance (I'm not 'puter efficient) and did: wlan0. 

After 

sudo service ntop restart

localhost:3000 showed activity. So, I kinda solved it with only a gentle push from the ntop people.

If you are trying to use ntop as a bandwidth monitor edit the file:

sudo gedit /var/lib/ntop/init.cfg

from 

eth0

to wlan0

that is eth-zero (the number) to wlan0 (again, the number, not the letter o as in Ohio).

---

