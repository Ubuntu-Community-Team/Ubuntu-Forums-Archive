---
title: "Problem accessing three.co.uk"
date: 2016-04-11
forum: Networking &amp; Wireless
---

### Post by rob169 on 2016-04-11
Short version of the problem:

On a new install of Ubuntu 14.04 on my laptop I'm unable to access [http://www.three.co.uk](http://www.three.co.uk). Both Firefox and Opera give "connection reset" messages. If I boot the laptop with Windows 7, I have no problems accessing the site with either Opera or Internet Explorer.

Other computers on the network (Windows 7 and Windows XP) have no problems either so the problem seems to be in Ubuntu.

The problem is completely repeatable - for over a week, I can never get three.co.uk if I boot Ubuntu, but can always get it in Windows 7.

More detail

The laptop was wiped a few weeks ago and a new install of Windows 7 put on by someone else. Last week I added Ubuntu and have been using it as my main system. I've added a few packages but made very few changes so far, so it's pretty much a clean install. I haven't found any other websites giving problems.

This is on a home network with an Edimax router. Nothing has changed on the router in a long time. It's managed by me and is pretty much as it came - the only significant change being DNS servers different from my ISP's. I don't believe the problem to be DNS related - the behaviour is the same if I use a numeric IP address. I have tried rebooting the router.

I don't really know what to try next, so any help greatly appreciated. Oh, and sorry if this has come up before - it's very difficult to do any effective search for "three".

---

### Post by goofprog on 2016-04-11
You say nothing wrong with DNS.  Okay.  I would just reinstall firefox.  I know that some sites that are HTML5 enabled are a little strange in Linux.  Youtube was one of them.  Maybe update the browser to the latest one.  I am not sure if it will help.  It is just like flip a switch here and try flipping switches there and there.

---

### Post by rob169 on 2016-04-12
OK, tried reinstalling Firefox, didn't make any difference. Installed Midori, that doesn't work for three.co.uk either. With 3 different browsers -  Firefox/Opera/Midori - all up to date and showing exactly the same problem, I don't think it's anything to do with the browser.

Any other ideas anyone?

---

### Post by apohal9 on 2016-04-13
If the last significant change was related to DNS and since then access is not working, I'd suggest you change it back and see if it works again. Also try to compare to which IP both OS resolve the URL you like to access.

---

### Post by The Cog on 2016-04-13
Please will you run the following command just before you try the browser, and stop it with Ctrl-C when you get the connection reset error message, then post the output here. It traces the packets going over the wire.
```
sudo tcpdump -np
```
If you see no output, you may need to specify which interface to trace (get the interface name from network manager) like this:
```
sudo tcpdump -np -i wlan0
```

For reference, the IP address I resolve for that site is 92.41.252.3. No problem with firefox on Ubuntu 15.10.

---

### Post by rob169 on 2016-04-13
> **The Cog said:**
> 

For reference, the IP address I resolve for that site is 92.41.252.3. No problem with firefox on Ubuntu 15.10.

Same IP as I get, don't think that's the problem. 

I've noticed that in Opera that the reset consistently comes after 60 seconds. Firefox is a bit more erratic, but sometimes it's about the same. Some higher level timer resetting the connection because communications hasn't been established?

Thanks for your help.

tcpdump follows (this one's for Firefox).

```
sudo tcpdump -np -i wlan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes
21:17:38.676894 IP 192.168.2.100.60924 > 92.41.252.3.80: Flags [F.], seq 3801930727, ack 800108961, win 29200, length 0
21:17:38.681340 IP 192.168.2.100.11431 > 194.73.82.242.53: 16119+ A? www.three.co.uk. (33)
21:17:38.681369 IP 192.168.2.100.11431 > 208.67.220.220.53: 16119+ A? www.three.co.uk. (33)
21:17:38.681422 IP 192.168.2.100.16410 > 208.67.220.220.53: 63370+ AAAA? www.three.co.uk. (33)
21:17:38.681613 IP 192.168.2.100.44481 > 208.67.220.220.53: 29399+ A? www.three.co.uk. (33)
21:17:39.355880 IP 92.41.252.3.80 > 192.168.2.100.60924: Flags [R], seq 800108961, win 0, length 0
21:17:39.656728 IP 208.67.220.220.53 > 192.168.2.100.11431: 16119 1/0/0 A 92.41.252.3 (49)
21:17:39.765857 IP 208.67.220.220.53 > 192.168.2.100.16410: 63370 0/1/0 (117)
21:17:39.865961 IP 208.67.220.220.53 > 192.168.2.100.44481: 29399 1/0/0 A 92.41.252.3 (49)
21:17:39.866403 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [S], seq 2514032832, win 29200, options [mss 1460,sackOK,TS val 12593278 ecr 0,nop,wscale 7], length 0
21:17:40.008096 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 262
21:17:40.011699 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 334
21:17:40.015248 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 330
21:17:40.018654 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 310
21:17:40.022400 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 342
21:17:40.025974 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 324
21:17:40.029511 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:17:40.035888 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:17:40.116489 IP 192.168.2.100.60930 > 92.41.252.3.80: Flags [S], seq 4079720905, win 29200, options [mss 1460,sackOK,TS val 12593340 ecr 0,nop,wscale 7], length 0
21:17:40.197052 IP 92.41.252.3.80 > 192.168.2.100.60928: Flags [S.], seq 740022174, ack 2514032833, win 0, options [mss 1460], length 0
21:17:40.197103 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [.], ack 1, win 29200, length 0
21:17:40.397101 IP 92.41.252.3.80 > 192.168.2.100.60930: Flags [S.], seq 3927160598, ack 4079720906, win 0, options [mss 1460], length 0
21:17:40.397154 IP 192.168.2.100.60930 > 92.41.252.3.80: Flags [.], ack 1, win 29200, length 0
21:17:40.486028 IP 92.41.252.3.80 > 192.168.2.100.60928: Flags [.], ack 1, win 32768, length 0
21:17:40.486059 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:17:40.486080 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [P.], seq 1461:1771, ack 1, win 29200, length 310
21:17:40.665880 IP 92.41.252.3.80 > 192.168.2.100.60930: Flags [.], ack 1, win 32768, length 0
21:17:41.327020 IP 92.41.252.3.80 > 192.168.2.100.60928: Flags [.], ack 1, win 32768, length 0
21:17:41.408977 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:17:44.353853 ARP, Request who-has 192.168.2.100 tell 192.168.2.1, length 28
21:17:44.353877 ARP, Reply 192.168.2.100 is-at 6c:88:14:2f:36:60, length 28
21:17:46.128985 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:17:46.197677 IP 192.168.2.100.60930 > 92.41.252.3.80: Flags [F.], seq 1, ack 1, win 29200, length 0
21:17:46.405814 IP 92.41.252.3.80 > 192.168.2.100.60930: Flags [.], ack 2, win 32768, length 0
21:17:46.427226 IP 92.41.252.3.80 > 192.168.2.100.60930: Flags [F.], seq 1, ack 2, win 32768, length 0
21:17:46.427258 IP 192.168.2.100.60930 > 92.41.252.3.80: Flags [.], ack 2, win 29200, length 0
21:17:55.552955 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:18:14.432962 IP 192.168.2.100.60928 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:18:19.440953 ARP, Request who-has 192.168.2.1 tell 192.168.2.100, length 28
21:18:19.442781 ARP, Reply 192.168.2.1 is-at 00:1f:1f:6d:9c:90, length 28
21:18:40.016129 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 262
21:18:40.019727 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 334
21:18:40.023375 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 330
21:18:40.026782 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 310
21:18:40.030490 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 342
21:18:40.034055 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 324
21:18:40.040391 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:18:40.043918 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:18:40.245451 IP 92.41.252.3.80 > 192.168.2.100.60928: Flags [R.], seq 1, ack 1, win 32768, length 0
21:18:40.245994 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [S], seq 2150303742, win 29200, options [mss 1460,sackOK,TS val 12608373 ecr 0,nop,wscale 7], length 0
21:18:40.246269 IP 192.168.2.100.32372 > 194.73.82.242.53: 6420+ A? www.three.co.uk. (33)
21:18:40.246291 IP 192.168.2.100.32372 > 208.67.220.220.53: 6420+ A? www.three.co.uk. (33)
21:18:40.496496 IP 192.168.2.100.60934 > 92.41.252.3.80: Flags [S], seq 3198169477, win 29200, options [mss 1460,sackOK,TS val 12608435 ecr 0,nop,wscale 7], length 0
21:18:40.595348 IP 92.41.252.3.80 > 192.168.2.100.60932: Flags [S.], seq 1357631218, ack 2150303743, win 0, options [mss 1460], length 0
21:18:40.595399 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [.], ack 1, win 29200, length 0
21:18:40.795321 IP 208.67.220.220.53 > 192.168.2.100.32372: 6420 1/0/0 A 92.41.252.3 (49)
21:18:40.995338 IP 92.41.252.3.80 > 192.168.2.100.60934: Flags [S.], seq 445039755, ack 3198169478, win 0, options [mss 1460], length 0
21:18:40.995391 IP 192.168.2.100.60934 > 92.41.252.3.80: Flags [.], ack 1, win 29200, length 0
21:18:41.095248 IP 92.41.252.3.80 > 192.168.2.100.60932: Flags [.], ack 1, win 32768, length 0
21:18:41.095283 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:18:41.095304 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [P.], seq 1461:1771, ack 1, win 29200, length 310
21:18:41.315406 IP 92.41.252.3.80 > 192.168.2.100.60934: Flags [.], ack 1, win 32768, length 0
21:18:42.025404 IP 92.41.252.3.80 > 192.168.2.100.60932: Flags [.], ack 1, win 32768, length 0
21:18:42.112961 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:18:45.245835 ARP, Request who-has 192.168.2.100 tell 192.168.2.1, length 28
21:18:45.245867 ARP, Reply 192.168.2.100 is-at 6c:88:14:2f:36:60, length 28
21:18:45.995739 IP 192.168.2.100.60934 > 92.41.252.3.80: Flags [F.], seq 1, ack 1, win 29200, length 0
21:18:46.245222 IP 92.41.252.3.80 > 192.168.2.100.60934: Flags [.], ack 2, win 32768, length 0
21:18:46.265127 IP 92.41.252.3.80 > 192.168.2.100.60934: Flags [F.], seq 1, ack 2, win 32768, length 0
21:18:46.265160 IP 192.168.2.100.60934 > 92.41.252.3.80: Flags [.], ack 2, win 29200, length 0
21:18:46.640955 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:18:55.712973 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:19:10.020054 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 262
21:19:10.023631 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 334
21:19:10.027244 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 330
21:19:10.030707 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 310
21:19:10.034395 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 342
21:19:10.037990 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 324
21:19:10.044262 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:19:10.047873 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:19:13.824991 IP 192.168.2.100.60932 > 92.41.252.3.80: Flags [P.], seq 1:1461, ack 1, win 29200, length 1460
21:19:18.832949 ARP, Request who-has 192.168.2.1 tell 192.168.2.100, length 28
21:19:18.834891 ARP, Reply 192.168.2.1 is-at 00:1f:1f:6d:9c:90, length 28
21:19:40.024074 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 262
21:19:40.027719 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 334
21:19:40.031371 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 330
21:19:40.034762 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 310
21:19:40.038389 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 342
21:19:40.041926 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 324
21:19:40.048241 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:19:40.051772 IP 192.168.2.1.3073 > 239.255.255.250.1900: UDP, length 326
21:19:41.044839 IP 92.41.252.3.80 > 192.168.2.100.60932: Flags [R.], seq 1, ack 1, win 32768, length 0
21:19:43.091921 IP 192.168.2.100.27572 > 194.73.82.242.53: 42684+ A? support.mozilla.org. (37)
21:19:43.091953 IP 192.168.2.100.27572 > 208.67.220.220.53: 42684+ A? support.mozilla.org. (37)
21:19:43.092007 IP 192.168.2.100.22353 > 208.67.220.220.53: 22337+ AAAA? support.mozilla.org. (37)
21:19:43.504919 IP 208.67.220.220.53 > 192.168.2.100.27572: 42684 2/0/0 CNAME sumo.external.zlb.scl3.mozilla.com., A 63.245.213.32 (101)
21:19:43.574840 IP 208.67.220.220.53 > 192.168.2.100.22353: 22337 1/1/0 CNAME sumo.external.zlb.scl3.mozilla.com. (156)
21:19:46.049533 ARP, Request who-has 192.168.2.100 tell 192.168.2.1, length 28
21:19:46.049567 ARP, Reply 192.168.2.100 is-at 6c:88:14:2f:36:60, length 28
^C
99 packets captured
99 packets received by filter
0 packets dropped by kernel


```

---

### Post by The Cog on 2016-04-14
Hmm,

It's behaving as though large packets from firefox don't reach the other end. I wonder if you can prove that by reducing your MTU (max packet size you send). 
Try this command to temporarily reduce it (using the appropriate interface name):
```
sudo ifconfig eth0 mtu 1400
```

---

### Post by rob169 on 2016-04-14
> **The Cog said:**
> Hmm,

It's behaving as though large packets from firefox don't reach the other end. I wonder if you can prove that by reducing your MTU (max packet size you send). 
Try this command to temporarily reduce it (using the appropriate interface name):
```
sudo ifconfig eth0 mtu 1400
```
OK great, that's fixed it. Quick binary search shows that all is well at MTU 1440, 1441 doesn't work. Should I just edit this into /etc/network/interfaces and forget about it? 

I remain slightly mystified by: why it works for you in ubuntu (presumably your MTU is 1500 or more); why it works for me in Windows 7 and XP where MTU is definitely 1500. However the workround is so painless that it's not worth worrying about.

For the record for anybody encountering the same problem, ISP is Three Mobile Broadband - i.e. the oddity only seems to affect my path to my ISP's own website. It doesn't seem to affect access to my ISP's website via other ISPs or my access to any other website.

Thanks again for your help.

---

### Post by The Cog on 2016-04-14
That really is peculiar. Only from your isp to their own website. I wonder if they have some kind of VPN encapsulation in the path for their own users to their own website, and the extra encpsulation is tsking the packets over a 1500 limit somewhere. But then, why doesn't it affect windows connections? I don't know. I wonder if Linux's use of the wscale (window size scaling) option is breaking things - maybe a firewall in the middle doesn't know how to fragment packets properly when they use wscale? It's all just guessing.

I vaguely remember there is a way to disable use of wscale, but don't remember where I saw it - I guess that's a googling job if you want to try it.

---

### Post by rob169 on 2016-04-14
> **The Cog said:**
> That really is peculiar. Only from your isp to their own website. I wonder if they have some kind of VPN encapsulation in the path for their own users to their own website, and the extra encpsulation is tsking the packets over a 1500 limit somewhere. But then, why doesn't it affect windows connections? I don't know. I wonder if Linux's use of the wscale (window size scaling) option is breaking things - maybe a firewall in the middle doesn't know how to fragment packets properly when they use wscale? It's all just guessing.

I remember concluding a while back that Three relied on a VPN though can't remember why I decided that.

> **The Cog said:**
> I vaguely remember there is a way to disable use of wscale, but don't remember where I saw it - I guess that's a googling job if you want to try it.

Basically ```
 echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

But this didn't seem to make any difference. (Though my understanding of /proc is a bit hazy, so maybe what I did didn't have any effect.)

After some further thought, I remembered that access to three.co.uk was always rather slow under Windows. I rarely go to the home page - my main need is to access a subpage to do with my account. This automatically logs me in by recognizing where the connection is coming from, so I assumed that was what caused the slowness. 

However, with Ubuntu and MTU set to 1440, the connection and login work very quickly. So after reading round a bit, my interpretation is that under Windows, Path MTU Discovery solves the problem but it takes time. In Ubuntu, the discovery fails and the connection gives up. Path MTU Discovery works relies on ICMP messages which some networks suppress for security reasons. Some implementations therefore assume that dropped packets are caused by overlarge MTU rather than congestion and deal with it accordingly. If Windows does this and not Linux, that would explain the difference.

Does this make sense?  Thanks again for the help.

---

