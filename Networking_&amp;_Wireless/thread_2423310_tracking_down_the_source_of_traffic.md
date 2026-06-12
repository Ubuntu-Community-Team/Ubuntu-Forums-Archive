---
title: "tracking down the source of traffic"
date: 2019-07-20
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2019-07-20
something on my laptop is initiating some traffic from my laptop out to a google IP on port 443 (HTTPS) and getting a quick response, every few minutes, even when there are no instances of firefox running.  as far as i know, chrome is not installed.  i'd like to know what i can do to track down what process, uid, and executable file is doing this.  then i can make a judgement call of what to do about it.  maybe it's something i want to allow and just add to my standard [FONT=courier new]tcpdump[/FONT] blocking list (the list of stuff that i never want to see when doing [FONT=courier new]tcpdump[/FONT]).

---

### Post by TheFu on 2019-07-20
lsof and netstat

---

### Post by The Cog on 2019-07-20
If it's a brief connection then it will be difficult to catch with lsof or netstat. You will improve your chances if you use iptables to block the connection. Then the connection will get stuck in the SYN_SENT state for several seconds until it times out - this will be easier to spot. Having configured iptables to drop the connection packets (drop tcp dstport 443 for instance), this command may help spot it when it happens:
```
sudo watch ss -tp | grep SYN-SENT
```
EDIT:
As an afterthought, in case anyone else likes this idea: The above only leaves the output on the screen for 2 seconds. Below is one you can walk away from and see later:
```
while true; do sudo ss -tp | grep SYN-SENT ; sleep 1 ; done
```

And it's SYN-SENT, not SYN_SENT as I originally posted.

---

### Post by TheFu on 2019-07-20
Good point. 

Lots of perfectly valid programs use HTTPS for communications thanks to the switch to micro-services. 
Which IP? What are the source and target ports? UDP/TCP?
More and more companies are running stuff on google's cloud, for example [http://connectivity-check.ubuntu.com](http://connectivity-check.ubuntu.com) goes to there.  It can be disabled.

---

### Post by Skaperen on 2019-07-20
it apparently is brief.  i have used [FONT=courier new]lsof[/FONT] and [FONT=courier new]netstat[/FONT] but they catch nothing.  [FONT=courier new]tcpdump[/FONT] sees it but by then it is just a few network packets.  i am trying to layer it through a few tunnels to slow it down, but even that is not working.  i'm trying to build a UDP slowdown relay to add lag to an [FONT=courier new]OpenVPN[/FONT] tunnel.[FONT=arial][/FONT]

the SYN_SENT idea sounds good.

i wish the kernel had a way to open a special pipe that would deliver a copy of every syscall by all other processes (except pid 1).  then someone could create a [FONT=courier new]sycalldump[/FONT] program.

---

### Post by Skaperen on 2019-07-20
the SYN_SENT idea worked.  i did it with [FONT=courier new]netstat[/FONT] and it shows python3, so it is some python3 script.  now i will use [FONT=courier new]lsof[/FONT] or [FONT=courier new]ps[/FONT] to see more.

---

### Post by Skaperen on 2019-07-20
turns out to be a cron script of my own that i didn't record the IPs for, because there were too many IP ranges.  it is really picking up incoming email that gets deposited in AWS S3 by AWS SES.  it runs every 10 minutes.  yes, i have seen some very fast response from S3.

i can't easily filter these from my [FONT=courier new]tcpdump[/FONT] runs when i need to see port 443, due to so many ranges at AWS. so, i need to add a way to suspend the script when i am doing [FONT=courier new]tcpdump[/FONT].  maybe i'll have the script run [FONT=courier new]ps[/FONT] and if [FONT=courier new]tcpdump[/FONT] is running then sleep a few seconds and try again.

---

