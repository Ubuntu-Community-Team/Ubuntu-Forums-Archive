---
title: "10 sek difference in time on 2 machines with NTP"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by Azyx on 2013-11-04
I have 2 Ubuntu 12.04LTS machines with syncroonizing to internet (NTP) activated, but I get 10 seconds in difference between the machines. They are on my home network using same gateway/router/broadbands sharer. 

Can I have different NTP-servers on the machines?

How do I find that?

Cheers

---

### Post by tgalati4 on 2013-11-04
One machine might have a dead motherboard battery or a slow real-time-clock (rtc).  How old are these machines?  Clocks slow down over time as the quartz crystal ages.

NTP updates the system clock periodically (I think once an hour by default) and assumes that your rtc is working correctly.  You can set up ntp to calculate 2nd order drift--thermal up and down to keep more accurate time (down to a millisecond!)  but again it relies on a working, stable rtc.  

You can try different time servers on each machine to see if it makes a difference.  Generally all of the ntp time servers are accurate to 1 second at any time of the day.  Anything beyond that usually indicates a problem.

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

[http://manpages.ubuntu.com/manpages/raring/man5/ntp.conf.5.html](http://manpages.ubuntu.com/manpages/raring/man5/ntp.conf.5.html)

---

### Post by Azyx on 2013-11-04
2 and 5 years. But if they synk via NTP-server , does not the hardware clock resets?

What does "sudo hwclock" tell you?

---

### Post by tgalati4 on 2013-11-04
tgalati4@Mint14-Extensa ~ $ sudo hwclock
[sudo] password for tgalati4: 
Mon 04 Nov 2013 09:34:21 AM PST  -0.139147 seconds

If your clock is broken, you may lose several seconds per hour.

Your clock should be no more than + or - one second from the ntp servers.  Now, sometimes network latency will throw a clock off, but not 10 seconds. 

Compare both machines to a cell phone or a cable box.  Which machine is off by 10 seconds?  Turn logging on in /etc/ntp.conf and examine the logs after a few hours.

Check the drift file of both machines:

tgalati4@Mint14-Extensa ~ $ cat /var/lib/ntp/ntp.drift
4.446

This represents parts per million (PPM) of linear offset that is applied each hour to keep the rtc and the ntp syncronized.  It is computed and adjusted each hour as well.  Most quartz clocks vibrate at 32768 Hz.  So with a little math you can calcuate what your actual quartz crystal is oscillating at.  It also varies with temperature, so second-order corrections are applied if they are enabled in the configuration file.

---

### Post by Azyx on 2013-11-07
I don't have any /var/lib/[COLOR=#0000cd]**ntp**[/COLOR] folder in my install with Ubuntu 12.04LTS on any of my 3 machines. There are just an empty folder called **[COLOR=#0000cd]ntpdate[/COLOR]** between folders Network manager and nvidia. But on my Lubuntu 13.10 on an eee PC 900 I have /var/lib/ntp/[COLOR=#0000cd]ntp.drift[/COLOR] and it is 2,736.

The time-diff between my computers+phone are -22, -20, -18 and one +4 seconds compared to one computer. There seems to be 2 diffentent times with approximatly 20 seconds between the.

I just now I'm only may chois between manual and automatic in time setting. Ones up on a time, I think you should select an NTP-server near you, but I can not find it any more.
Cheers

PS. sudo hwtime give me someting between -0,5 to -0,9 seconds on my  4 machines.

---

### Post by tgalati4 on 2013-11-07
Is ntp running?

tgalati4@Mint14-Extensa ~ $ ps -ef | grep ntp
ntp      30606     1  0 06:47 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 105:110
tgalati4 30863 23076  0 06:57 pts/0    00:00:00 grep --colour=auto ntp

If you enable statistics, then you will get some files in /var/log/ntpstats.

---

### Post by ian-weisser on 2013-11-07
NTP won't correct large differences (like over a full second). The developers assume there is some non-NTP error at work if your clock is that far off, and don't want to mistakenly propagate that issue across your network. 
You must run ntpdate manually to re-sync your system, then NTP will keep the clocks working together. See man ntpdate for easy instructions.

Large differences in time can accrue if your system is offline for an extended period (motherboard clock), or if you choose a lousy set of upstream servers that disagree, are themselves off, or are otherwise flaky.

---

### Post by Azyx on 2013-11-10
Have not doing anything, but now 3 off the clocks are within 1 sec.

---

### Post by ian-weisser on 2013-11-10
That's great!
Perhaps NTP has improved since I last had a similar problem.

---

### Post by Azyx on 2013-11-10
really strange. all of my machines are now quite time syncronised, less than a second.

---

### Post by tgalati4 on 2013-11-10
So things are working as they should.  Ntp generally works well, out-of-the box, without having to do anything.  If you really want to get accurate time, then play around with the statistics.  You can get down to a few milliseconds--even sub-millisecond.

---

