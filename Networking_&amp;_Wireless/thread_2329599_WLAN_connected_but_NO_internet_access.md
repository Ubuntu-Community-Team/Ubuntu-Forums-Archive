---
title: "WLAN connected but NO internet access"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by mamboknave on 2016-07-03
Greetings.

Sorry, the title is wrong. It's not WLAN, it is ETH1.

I am with release 12.04 and kernel 3.5

After recent, small updates to the OS and some additional packages, I suddenly cannot access to internet. It worked for years.

I am fully connected/wired with ETH1. I can ping the gateway successfully, as well as 127.0.0.1 (which I do not know what it is).

The file /etc/resolv.conf contains:

nameserver  192.168.7.2
nameserver  192.168.1.241
search eng.myemployer.com

Ping to any of these fails totally.

Can anyone help, please?

Thanks a lot!

---

### Post by TheFu on 2016-07-04
Likely a bad router, bad switch port, bad cable. Swap those out first.  If you can ping the gateway, then the Ubuntu system is probably working correctly. Look for issues outside of ubuntu.

Can you ping 8.8.8.8? This is a well-known IP.  That will help to determine if the issue is internet connectivity or just DNS as the root cause.

BTW, the 192.168.x.x IPs don't mean anything special. Do you know that a DNS is running on those IPs?

And 12.04 core support ends in less than a year. Most of the upstream program support ended a few years ago already. Perhaps it is time to migrate to a newer LTS?

---

### Post by mamboknave on 2016-07-04
Thanks! I corrected the title although, the problem is identical when connected ETH1 or WLAN. Does not matter.

Yes, 8.8.8.8 pings with no losses.

>> BTW, the 192.168.x.x IPs don't mean anything special. Do you know that a DNS is running on those IPs?

I have no idea what you mean/ask. Sorry. My gateway is 192.168.0.1

By the way, I have a PC wire-connected and phones WiFi connected with no problems at all. All to the same router.

Also, it all started after having nstalled some VPN packages. Among the processes I see [/usr/sbin/sshd -D] and [/usr/bin/ssh-agent ......]

---

### Post by TheFu on 2016-07-04
If you can ping 8.8.8.8, then it isn't a connectivity issue. It is a DNS problem.  Use different DNS by editing the /etc/resolv.conf with a new server.  Use the DNS that the Windows machine or phone uses - or use any of the reputable, public, DNS servers.  Google has one which is relatively fast, but do you trust google with all that metadata?

---

### Post by mamboknave on 2016-07-04
Thank You. I see what you mean.

---

