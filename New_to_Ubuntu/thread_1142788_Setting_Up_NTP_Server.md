---
title: "Setting Up NTP Server"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by rschapman on 2009-04-29
Here at the University we have a touch control panel that will not sync time with Windows Domain Controllers. What do I need to do to setup a Ubuntu system to simply serve time to these devices? They will not sync with anything not on the LAN so it has to be a local option. Thanks.

---

### Post by cmnorton on 2009-04-29
For starters enter

sudo apt-get install -y ntp

Then man ntp to learn more and have a looksie at /etc/ntp.conf. (Of course you'll edit it as sudo.)

---

### Post by rhcm123 on 2009-04-29
> **rschapman said:**
> Here at the University we have a touch control panel that will not sync time with Windows Domain Controllers. What do I need to do to setup a Ubuntu system to simply serve time to these devices? They will not sync with anything not on the LAN so it has to be a local option. Thanks.

It's a good idea to setup the NTP server as the DHCP server, or to tell your DHCP server to use the time-servers option. Run the following to grab the servers:
```
sudo apt-get install dhcp3-server ntp
```

Then edit the config files i've provided to suit your subnet.

DHCP:
```
# /etc/dhcp3/dhcpd.conf
# WRITTEN BY USSR 12 APRIL 2009

# SUBNET 1 OPTIONS
INTERFACES="eth0";
default-lease-time 600;
max-lease-time 7200;
	
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.2.255;
option routers 192.168.2.1;
option domain-name-servers 71.250.0.12, 68.237.161.12;
**option ntp-servers 192.168.2.193, pool.ntp.org;**
option domain-name "marchini.dyndns.org";
authoritative;

# MAIN SUBNET 1 CONFIG
subnet 192.168.2.0 netmask 255.255.255.0 {
	authoritative;
	range 192.168.2.200 192.168.2.250;
	}

```

NTP - I didn't really write my own, just copied the example file :D. You have to talk to an Internet server to get the correct time - i listen to the main ubuntu server, the main ntp.org server, and the main united states ntp.org server.
```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help
# WRITTEN BY USSR
# LAST MODIFIED 28 APRIL 2009

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com
server pool.ntp.org
server 0.us.pool.ntp.org


# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
restrict 192.168.2.0 mask 255.255.255.0 trust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.2.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

---

