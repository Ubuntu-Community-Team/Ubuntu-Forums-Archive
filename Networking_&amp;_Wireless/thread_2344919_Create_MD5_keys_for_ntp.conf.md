---
title: "Create MD5 keys for ntp.conf"
date: 2016-11-29
forum: Networking &amp; Wireless
---

### Post by dcos on 2016-11-29
Hi,

I've been trying to add authentication keys to my ntp.conf without any success if anyone can help.

I have installed and setup ntp based on this post [http://blogging.dragon.org.uk/setting-up-ntp-on-ubuntu-14-04/](http://blogging.dragon.org.uk/setting-up-ntp-on-ubuntu-14-04/)
And now trying to add md5 keys to the servers based on this post [http://www.ntp.org/ntpfaq/NTP-s-config-adv.htm](http://www.ntp.org/ntpfaq/NTP-s-config-adv.htm)

As a result I have modified the ntp.conf from the original and created ntp.keys

when I restart the server and check ntpq -cpe -cas I get bad authentications on my servers and I've no idea why. If anyone spots my mistake it will be greatly appreciated.

ind assid status  conf reach auth condition  last_event cnt
===========================================================
  1  4170  c02c   yes    no   bad    reject              2
  2  4171  c02c   yes    no   bad    reject              2
  3  4172  c02c   yes    no   bad    reject              2
  4  4173  c02c   yes    no   bad    reject              2
  5  4174  9024   yes   yes  none    reject   reachable  2
[B]
Looks Like I can't attach the files so contents of ntp.conf is:[/B]
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for
# more information.
# Modified from Original Added keys to servers
server 0.ubuntu.pool.ntp.org key 1
server 1.ubuntu.pool.ntp.org key 2
server 2.ubuntu.pool.ntp.org key 3
server 3.ubuntu.pool.ntp.org key 4

# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com

# modified from original added path for key file
keys /etc/ntp.keys

# modified from original defined keys
trustedkey 1 2 3 4 # define trusted keys
requestkey 15    # key (7) for accessing server variables
controlkey 15    # key (6) for accessing server variables

authdelay 0.000094      # authentication delay (Sun4c/50 IPX
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
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

**Contents of ntp.keys is:**
# Keys File
1    M    test1
2    M    test2
3    M    test3
4    M    test4
15    M    test5

---

### Post by evilmoo on 2017-07-05
Have you tried adding 15 to trustedkeys?

---

