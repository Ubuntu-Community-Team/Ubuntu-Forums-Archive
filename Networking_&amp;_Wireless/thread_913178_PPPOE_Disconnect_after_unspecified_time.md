---
title: "PPPOE Disconnect after unspecified time"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by haneya on 2008-09-07
Hi ..

am using pppoe with my ADSL modem (sagem fast 1201) by using "sudo pppoeconf" and it works fine but after minutes or hours the connection not responding at that time using "plog" return nothing to me and i cant browse any web page but the weird thing is torrent downloading and uploading normally but not that fast and Emesene works , after this happens i have to use "pon dsl-provider" and some times i have to shut down the connection and start again , this problem disturbs me very much am hoping that you guys can help me about it ; thanks 

idont know if this helps:(Dsl-provider content)```

# Configuration file for PPP, using PPP over Ethernet 
# to connect to a DSL provider.
#
# See the manual page pppd(8) for information on all the options.

##
# Section 1
#
# Stuff to configure...

# MUST CHANGE: Uncomment the following line, replacing the user@provider.net
# by the DSL user name given to your by your DSL provider.
# (There should be a matching entry in /etc/ppp/pap-secrets with the password.)
#user myusername@myprovider.net

# Use the pppoe program to send the ppp packets over the Ethernet link
# This line should work fine if this computer is the only one accessing
# the Internet through this DSL connection. This is the right line to use
# for most people.
#pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"

# An even more conservative version of the previous line, if things
# don't work using -m 1452... 
#pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1412"

# If the computer connected to the Internet using pppoe is not being used
# by other computers as a gateway to the Internet, you can try the following
# line instead, for a small gain in speed:
#pty "/usr/sbin/pppoe -I eth0 -T 80"


# The following two options should work fine for most DSL users.

# Assumes that your IP address is allocated dynamically
# by your DSL provider...
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
# Comment out if you already have the correct default route installed.
defaultroute

##
# Section 2
#
# Uncomment if your DSL provider charges by minute connected
# and you want to use demand-dialing. 
#
# Disconnect after 300 seconds (5 minutes) of idle time.

#demand
#idle 300

##
# Section 3
#
# You shouldn't need to change these options...

hide-password
lcp-echo-interval 20
lcp-echo-failure 3
# Override any connect script that may have been set in /etc/ppp/options.
connect /bin/true
noauth
persist
mtu 1492

# RFC 2516, paragraph 7 mandates that the following options MUST NOT be
# requested and MUST be rejected if requested by the peer:
# Address-and-Control-Field-Compression (ACFC)
noaccomp
# Asynchronous-Control-Character-Map (ACCM)
default-asyncmap

plugin rp-pppoe.so eth0
user "my account"
```

---

### Post by haneya on 2008-09-08
well i tried to use rp-pppoe it looks good and solving MTU and MSS problem ,but should i use it instead of pppoeconf or with it because some times the connection working and some times not , maybe i should to remove pppoeconf and its setting plz help me 

(now my pppoe connetion is not working at all "plog" return me that the connection is work but in fact nothing work )

---

### Post by tzily on 2011-07-05
if anyone is searching for this, editing the /etc/ppp/options file worked for me

> lcp-echo-interval 0
  lcp-echo-failure 0

i have broadband connecting through pppoe and it always disconnects  forever if i renew the dynamic ip using sudo poff and sudo pon  dsl-provider

---

