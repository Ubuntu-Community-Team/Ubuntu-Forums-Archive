---
title: "Bandwidth Limits: Looking for way to monitor what is using network traffic"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by finny388 on 2014-04-03
I'm running xubuntu 12.04. probably will switch to 14.04 in the summer.
I'd like to know what programs on what devices are taking up my monthly bandwidth and have this to be stored in a spreadsheet.

I can't believe how unpopular this endeavour is with ISP traffic limits flourishing.

Are there no routers or devices that do this out of the box?

e.g. table:

For a given date range:
[B]Device....Protocol/App.........Down.....Up
[/B]PC..........Protocol/App 1.......50GB....5GB
PC..........Protocol/App 2.......50GB....5GB
PC..........Protocol/App 3......150GB....1GB
Smart TV.Protocol/App 1.......50GB....1GB
Tablet.....Protocol/App 1.........5GB....1GB
Tablet.....Protocol/App 2.......50GB....1GB
......................................355GB...14GB

Or if there is a good software that would just track my pc (breaking down which apps/protocols) that would be great. I could probably do the same thing on my tablet (nexus 7) and then deduce what the smart tv (netflix) is using

Any tips appreciated. Thanks.

---

### Post by TheFu on 2014-04-04
pfSense will, but only if all traffic goes through the pfsense router.
openwrt, tomato and ddwrt should have a monitoring plugin - same caveat - all traffic must go through the router.

---

### Post by finny388 on 2014-04-04
so it is a possible for a router (or software and router) to report which programs are using how much? Or is it divided by type of traffic? Sorry, networking is not my specialty.

---

### Post by TheFu on 2014-04-04
No. It is possible for the specific ports used to be reported by IP address.  Tomato has the most user-friendly interface based on the last time I used it.  pfSense has the most real capabilities, however.

If a business can't afford an expensive firewall like a Nokia, then they deploy pfSense.

---

### Post by finny388 on 2014-04-13
I'm using vnstat now to at least isolate what the pc is responsible for.
If I could just break it down by type of traffic, that would be awesome.

I have an old netbook (eee 900). Could it be used to route and monitor traffic with more detail than vnstat?
It seems if that's possible it should be possible to have the monitoring done on the pc

---

### Post by The Cog on 2014-04-13
It would be worth looking at ntop. 
Unless you have a hub rahter than a repeater (unlikely) you would also need to route all the other PCs through yours in order to see what they are doing too. ntop will give you a lot of detail about which ports (and therefore which protocols) were used, but cannot tell you which application in the machine was responsible.

---

### Post by untrustytahr on 2014-04-13
***nethogs*** will give you the bandwidth per application but you would need to run it on each computer you wanted to monitor.

---

### Post by finny388 on 2014-04-13
I installed ntop with Synaptic
It says it runs in a browser but I don't how to launch it
I typed 'ntop' into terminal and got this:
```
Sun Apr 13 17:19:10 2014  NOTE: Interface merge enabled by default
Sun Apr 13 17:19:10 2014  Initializing gdbm databases
Sun Apr 13 17:19:10 2014  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Sun Apr 13 17:19:10 2014  Possible solution: please use '-P <directory>'
Sun Apr 13 17:19:10 2014  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Sun Apr 13 17:19:10 2014  CLEANUP[t139697826908288]: ntop caught signal 2 [state=2]
Sun Apr 13 17:19:10 2014  ntop is now quitting...

```

how do i set this up?

---

### Post by The Cog on 2014-04-15
I forget which port it listens on : try this command:
sudo netstat -lntp

A quick google says the default port is 3000, so connect to this in your browser:
[http://127.0.0.1:3000](http://127.0.0.1:3000)

---

### Post by finny388 on 2014-04-17
That did it
Now to learn ntop

To config it asks for a username/pw

Is this my router, OS or is this to create a ntop account?

---

### Post by Mama_Hadija on 2014-04-18
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
                [TD="class: answercell"]                  It's quite easy! install "iftop" with:
      sudo apt-get install iftop
  Then run
      sudo iftop
  from any terminal!
  Enjoy!
      
[/TD]
[/TR]
[/TABLE]

---

