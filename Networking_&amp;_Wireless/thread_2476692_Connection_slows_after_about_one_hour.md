---
title: "Connection slows after about one hour"
date: 2022-07-03
forum: Networking &amp; Wireless
---

### Post by aquaman101 on 2022-07-03
Hi, I'm new to Ubuntu and I'm struggling with a Wi-fi network connection issue that shows up roughly after one hour of use.

So my connection speed goes from 40Mbps to around 300Kbps. Doesn't matter which browser I use (Firefox or Brave) and it happens every time after laptop has been on for one hour. If I re-boot everything is OK again, until one hour later when the same thing happens again.

I have tried multiple suggestions from other sites including turning off wifi power save mode but no change. The only solution I have found (other than rebooting) is to go into Wifi settings and disable ipv6. Now, I'm sort of semi computer literate, but I have no idea what ipv6 does or whether I need it???

Any help much appreciated

---

### Post by DuckHook on 2022-07-04
Welcome to the forums, aquaman101.

Network issues are usually cussed and complex.

Kudos to you for chasing it down to IPV6.

The short answer is: you don't really need IPV6 (yet), so turning it off is fine.

The longer answer is:

IPV6 was created some time ago because the world is running out of IPV4 addresses. While it is steadily increasing in adoption, it has not yet reached the state where failing to implement it is debilitating. Almost all important web sites still use IPV4. Therefore, you are unlikely to run into any noticeable problems if you disable it.

As time goes by, this state of affairs won't last. The world is truly running out of IPV4 addresses. IPV6 is so much larger that it is inconceivable that it will run out of addresses in our lifetimes. But I suspect that for the next three or four years at least, IPV4 will still continue to function entirely adequately.

At some point in the mid term future, it will be necessary to switch IPV6 back on. But this is not an immediate concern and you can keep it off for another few years, at which point, Ubuntu will have gone through so many updates that your slowdown will likely be fixed in the natural course of updating and with no further action from you.

Therefore, I recommend that you turn IPV6 off, keep it off, and forget about it for now.

If you want to chase down the problem purely as an intellectual exercise, then the first thing I would suggest is to look at your logs. Whenever any process goes pear shaped after starting out okay, the immediate place to check is your logs after pinpointing the exact time that the slowdown occurred. That's the point in your logs that you want to examine with a fine toothed comb.

---

### Post by DuckHook on 2022-07-04
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by aquaman101 on 2022-08-07
Unfortunately turning off ipv6 hasn't worked in the long run, and I am still facing the same connectivity issue - to the point were I have stopped using the laptop.

Being a complete newbie to ubuntu could anyone please tell me what I might be looking for in the logs - as when its happened today there is a lot of info in the log that doesnt make a lot of sense to me?

---

### Post by aquaman101 on 2022-08-19
Can anybody help with my internet connectivity issue (as explained in post#1)

I still have the issue and I am about to give up on Ubuntu (I even done the upgrade to Jammy Jellyfish with no change)

Last report message on error log is 67 instances of:

09:16:34 kernel: [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=5369 DF PROTO=2

---

### Post by aquaman101 on 2022-08-19
more info from a later crash


11:38:33 kernel: [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=58530 PROTO=UDP SPT=58596 DPT=5353 LEN=51 
11:38:33 kernel: [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=58530 PROTO=UDP SPT=58596 DPT=5353 LEN=51 
11:38:14 kernel: [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=32572 DF PROTO=2 
11:37:09 kernel: [UFW BLOCK] IN=wlp3s0 OUT= MAC=74:c6:3b:7a:38:ed:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=192.168.1.74 LEN=71 TOS=0x00 PREC=0x00 TTL=64 ID=41331 PROTO=UDP SPT=53320 DPT=5353 LEN=51 
11:36:23 kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
11:36:23 kernel: wlp3s0: associated
11:36:23 kernel: wlp3s0: associated
11:36:23 kernel: wlp3s0: RX AssocResp from 34:db:9c:d3:22:4f (capab=0x411 status=0 aid=1)
11:36:23 kernel: wlp3s0: associate with 34:db:9c:d3:22:4f (try 1/3)
11:36:23 kernel: wlp3s0: authenticated
11:36:23 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 1/3)
11:36:23 kernel: wlp3s0: authenticate with 34:db:9c:d3:22:4f
11:36:21 kernel: wlp3s0: authentication with 34:db:9c:d3:22:4f timed out
11:36:21 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 3/3)
11:36:21 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 2/3)
11:36:21 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 1/3)
11:36:21 kernel: wlp3s0: authenticate with 34:db:9c:d3:22:4f
11:36:20 kernel: wlp3s0: authentication with 34:db:9c:d3:22:4f timed out
11:36:20 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 3/3)
11:36:20 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 2/3)
11:36:20 kernel: wlp3s0: send auth to 34:db:9c:d3:22:4f (try 1/3)
11:36:20 kernel: wlp3s0: authenticate with 34:db:9c:d3:22:4f
11:36:12 kernel: wlp3s0: deauthenticating from 34:db:9c:d3:22:4f by local choice (Reason: 3=DEAUTH_LEAVING)
11:36:09 kernel: [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:34:db:9c:d3:22:52:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=2163 DF PROTO=2

---

