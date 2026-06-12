---
title: "Ubuntu on notebook - tedious switching between networks"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by qvx on 2006-09-07
Hi everybody,

I'm using Ubuntu on notebook and have to constantly switch between three networks:
[LIST=1]
[*] at work via eth0 (static ip, gateway, dns)
[*] at home1 via wireless eth1 (dhcp)
[*] at home2 via wireless eth1 (static ip, gateway, dns, wireless key)
[/LIST]

Everything is working but the process is slow and tedious because I have to change:
[LIST=1]
[*]network (interface+ip+netmask+gateway)
[*]DNS server
[*]Proxy server
[/LIST]

I'm currently using GUI tools like NetworkManager, Wifi-Radar and Network Proxy. Since this is a Linux, I would like to make three scripts to do this for me. NetworkManager is also very slow and it takes around a minute for the hourglass to disappear. And there is also the task of setting the proxy.

My idea was:
[LIST=1]
[*]save/prepare three versions of /etc/network/interfaces configuration file
[*]copy appropriate version of interfaces file
[*]somehow set DNS server
[*]somehow set proxies
[*]somehow restart networking
[/LIST]

**DNS server**
I found out that the information is written in /etc/resolv.conf but I don't know how to properly modify the value (is overwriting the file enough). Also in one of my combinations I'm using DHCP so I don't think that I should be setting up the DNS by myself.

**Proxy**
There is an environment variable http_proxy which gets set by the Network Proxy applet, but I'm not sure if that is all that it takes and how to set this variable globally so it affects entire system and not just the current bash shell (I don't thing that export is enough).

**Network restart**
I sometimes use ifdown/ifup commands. I've also seen somebody mention something like /etc/init.d/networking restart. What is the right way considering all the steps that I'm trying to accomplish?


While on Windows I'm using IBM Connection Manager (or something with similar name) where all this can be set up in advance and then changed with two mouse clicks. I tried numerous Linux tools (spent few days browsing through synaptic) which would be able to to the similar thing but they all offer partial functionality. I tried so many that I forgot their names, but being a programmer who recently decided to try Linux I think that doing this via shell scripts would be way cooler.


Thanks for any help

---

### Post by gborzi on 2006-09-07
There are some packages that, once configured, are able to automatically detect in which environment you are and update the network configuration accordingly. I have used two such programs:
whereami and guessnet+ifplugd+resolvconf.
The former gives you a lot of flexibility in configuration (or maybe too much, it's a matter of taste), the latter integrates better with ifupdown and is able to detect cable plugging and unplugging (thanks to ifplugd). Both of them are documented in the forums.

---

