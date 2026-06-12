---
title: "Waiting for network configuration"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by SebasSBM on 2014-06-19
Every time I boot up my laptop with Ubuntu 12.04 the message 'waiting for network configuration' annoys me. Before I didn't use to have this problem, but, since a lightning toasted my router and my ISP brought me a new one, my Ubuntu system is having this problem. It's really annoying ](*,)

I've spent lots of hours searching in the internet how to fix this, and I didn't find nothing that solves my problem. What I know is the following:

When it finally boots without full network configuration, the wireless network is not working (the interface I use). But, **all** **I have to do**[B] to fix this once the system is booted is starting network-manager:

[/B]```
sudo service network-manager start
```

But it's annoying anyway: every time I boot the system to be waiting 2 minutes for the "waiting for network configuration" messages.

I've been using Ubuntu for almost a year. I've made so much configuration changes that I just can't remember. I would like to know how to setup the correct network interface to be started while booting, but, after searching like crazy, I don't find nothing on the Internet about this. Before all this happened I had static IP configuration through /etc/network/interfaces and DNS servers through /etc/resolv.conf . Now, even if I set up both interfaces (eth0 and wlan0) to dhcp instead of static, not even this solves the problem.

**So the questions are: **what should I do? Which config files should I look at? which commands should I use? which logs should I look at to see what is failing at all? Summarizing: anything useful in this situation.

For now I'm going to disable *sleep* commands in failsafe.conf as a provisional solution. But the actual problem is that my network configuration is a mess, and I want to tidy it up to have a clean and simple network configuration again without having to reinstall Ubuntu. Any help is appreciated.

Thanks in advance

---

