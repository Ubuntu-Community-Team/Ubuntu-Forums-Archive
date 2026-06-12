---
title: "weird adsl error"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by genjix on 2006-12-05
Hi,

after using gentoo for the last few years and having recently suffered a broken system after a portage update I've decided to test the waters a bit with kubuntu.

Here is my script for connecting.

```

# /etc/ppp/peers/adslscript
# example configuration for the kernel space PPP over Ethernet driver
#
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "amir.t@hg1.btinternet.com"

# Load the PPPoE plugin.
plugin pppoatm.so
0.38

# Ethernet interface to which the modem is connected.
#eth0

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

debug

```

After I call "sudo pppd call adslscript" I get 

```

ppp0      Link encap:Point-to-Point Protocol
          inet addr:81.152.252.114  P-t-P:217.47.90.186  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:64 (64.0 b)  TX bytes:97 (97.0 b)

```

... but nothing connects, until I ping my external ip address (217.47.90.186) and everything is fine. If I try to ping beforehand I get "operation not permitted".

Any ideas? Thanks.

---

