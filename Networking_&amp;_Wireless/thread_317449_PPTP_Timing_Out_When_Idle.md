---
title: "PPTP Timing Out When Idle"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by David Mulligan on 2006-12-12
Only 2 days after I thought I had PPTP working well I find out otherwise.  

I am using network-manager-pptp to connect my Edgy laptop to my employer's Windows based vpn.  Above and beyond the standard "just set refuse EAP and it works" advice I had to set the MRU and MTU in order to get connected.  Then it seemed like all is good.

All was good until I left the machine connected overnight.  The nm-applet still showed me connected but I had no external connectivity until I disconnected the vpn.  Then network connectivity returned to normal and reconnecting to the vpn worked as expected.

I left lcp-echo-failure and lcp-echo-interval at the default values of 10.

I found this in the logs:
```

Dec 12 02:29:10 bordet pppd[7725]: LCP terminated by peer
Dec 12 02:29:10 bordet pppd[7725]: Connect time 58.4 minutes.
Dec 12 02:29:10 bordet pppd[7725]: Sent 5232120 bytes, received 225288613 bytes.
Dec 12 02:29:13 bordet pppd[7725]: Connection terminated.
Dec 12 02:29:13 bordet pppd[7725]: Modem hangup
Dec 12 02:29:13 bordet pppd[7725]: Exit.

```

Later on it disconnected after only 41 minutes.  I am guessing that the idle time it times out on is about 20 minutes.  More testing is required.

Is there any way to prevent it from timing out?

Is there any way for the nm-applet to discover that it has been disconnected?

Thanks,
David

---

### Post by David Mulligan on 2006-12-12
A little more research has led me to believe that my vpn connection times out after about 30 minutes of being idle.

I have a work around that has passed the first 30 minute interval.  I created a cronjob that pings something in the outside world every 5 minutes.  My employer's vpn is configured to route all non-local traffic through it.  This way my ping works whether I am on the vpn or not.

```
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /bin/ping -c 1 www.google.ca
```

---

### Post by swapnonil on 2006-12-14
Hi David,

I am having same problem but with PPoE, on my ADSL modem.

If I leave my internet connection idle for about 20 minutes, it **disconnects**.

I have to manually restart the connection using

```
sudo poff dsl-provider
```
and then
```
sudo pon dsl-provider
```

My settings for this dsl-provider as found in /etc/ppp/peers is like this.
```

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "swapnonil"

```

FYI I am using an Huawei SmartAX MT841 ADSL modem provided by BSNL's DataOne in India. I am running Edgy as of now, but the same problem use to occur in Dapper as well.

This is my interfaces file
```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# added by pppoeconf
auto eth0
iface eth0 inet dhcp

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

---

