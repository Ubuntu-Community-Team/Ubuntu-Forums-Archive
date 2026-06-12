---
title: "Cant connect to wired network."
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by powerse5 on 2007-05-10
I'm sorry if this has been posted before, I'm just a lowely noob.

I use Ubuntu 7.04 and my computer wont connect anymore to the router and cant get an IP address.  Last night I turned off my computer for the night and this morning I get nothing.  I plug in my windows laptop and its fine, even the laptop is ok on wireless, but not my Ubuntu desktop.  Anyone know what could have happened or what more information I need to give to try and get this resolved.

Thanks in advance. :)

---

### Post by dannyboy79 on 2007-05-10
> **powerse5 said:**
> I'm sorry if this has been posted before, I'm just a lowely noob.

I use Ubuntu 7.04 and my computer wont connect anymore to the router and cant get an IP address.  Last night I turned off my computer for the night and this morning I get nothing.  I plug in my windows laptop and its fine, even the laptop is ok on wireless, but not my Ubuntu desktop.  Anyone know what could have happened or what more information I need to give to try and get this resolved.

Thanks in advance. :)

well there is several things to check.you need to make sure that your dns server is set correctly. if it's not this will prevent you from accessing the internet. the best way to determine if it's a dns issue is that if you can ping google.com by ip address (64.233.167.104) then it's a dns issue. otherwise it's something else. things to check, is networking on.

```
sudo /etc/init.d/networking restart
```

do you have an ip address.

```
ifconfig -a
```

is your interfaces file correct?

sudo cat /etc/network/interfaces

should have a interface for lo and for your main interface like eth0 or eth1 if it's wired or wlan0 or ath0 or rausb0 if it's wireless. let me see the output from entering these commnds in a terminal also.

```
dmesg | grep Eth
```

```
dmesg | grep eth
```

```
lspci -v
```

```
lsusb -v
```

do you have a router? or just a cable modem or dsl? also, if you have a router, is a true dns server or does it just forward the dns requests to your isp dns servers? most consumer level routers don't have built in dns servers unless you're renting it from cox or some other cable internet provider, so if it's just a cheaper netgear, belkin, lynksys you may need to add your isp's dns servers into the networking gui for your main interface. please post back everything I have asked for and answer all my questions if you'd like my help. if you don't know an answer, than please just say that so I know you didn't answer it because you didn't know the answer. I am stating this because many users will just post back and not answer my querstions and then I have to ask for the info again. people can't expect for some1 to provide them help if they don't help the person help them. i don't know your setup hence why I am asking qeustions to get an idea of how to help you. looking forward to helping you. also, are you using a static ip or dynamic and are you using vpn or not? are you using network-manager applet (network thing in upper right corner of ubuntu)

---

