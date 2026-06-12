---
title: "NTP Server Not In Sync"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by LRT on 2009-07-29
I have a server running ntpd and somehow the date and time on that server is not correct. It is about 3 minutes behind. All samba clients are time synced to this server which means now all my clients are 3 minuted behind.

I tried runnning ntpd -b, but the time is stil 3 minutes behind.

How do I fix this??

---

### Post by Zill on 2009-07-29
I just installed ntp and ntpdate then edited /etc/ntp.conf to include my local (UK) servers:

server 0.uk.pool.ntp.org
server 1.uk.pool.ntp.org
server 2.uk.pool.ntp.org
server 3.uk.pool.ntp.org

Once file updated, restart ntp:
sudo /etc/init.d/ntp restart

Type the following to find out if ntp is working or not:
ntpq -p  (server name)
or
ntpq -pn  (server IP address)

One of the lines should start with an asterisk (*) which means your computer gets the time from the internet.

[https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")

---

### Post by LRT on 2009-07-29
Hi Zill,

Thanks for your reply. Here is what my ntp.conf file looks like:

```


# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.ubuntu.com
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
#restrict -4 default kod notrap nomodify nopeer noquery
#restrict -6 default kod notrap nomodify nopeer noquery
restrict -4 default kod notrap nomodify nopeer
restrict -6 default kod notrap nomodify nopeer

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


```

And this is the output of:

ntpq -p 0.us.pool.ntp.org

```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-otc1.psu.edu    .WWV.            1 u  495 1024  377    4.397  -18.415   0.317
+GPS1.net.cmu.ed .GPS.            1 u  782 1024  377    2.278   -0.017   0.061
*GPS0.net.cmu.ed .GPS.            1 u  396 1024  373    2.386   -0.036   0.029
-ntp-nasa.arc.na .GPS.            1 u 4971 1024  377   88.113    6.524   0.017
-ntp1.rrze.uni-e .DCFp.           1 u  156 1024  377  110.129   -2.214   0.009
-india.colorado. .ACTS.           1 u  588 1024  377   62.276    0.667   0.845
-A84-NS5.net.cmu 128.237.148.132  2 u  145 1024  377    0.368    0.120   0.143
+WEH-NS-1.net.cm 128.237.148.140  2 u   59 1024  377    0.230    0.005   0.066

```

But still my time is about 4 minutes behind ](*,)

Any more ideas?

---

### Post by Zill on 2009-07-29
> **LRT said:**
> ...
# By default, exchange time with everybody, but don't allow configuration.
#restrict -4 default kod notrap nomodify nopeer noquery
#restrict -6 default kod notrap nomodify nopeer noquery
restrict -4 default kod notrap nomodify nopeer
restrict -6 default kod notrap nomodify nopeer
...
I don't know if this will change things but my /etc/ntp.conf file uses the "noquery" options:
```
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery
```

---

### Post by LRT on 2009-07-31
I uncommented those lines in ntp.conf and restarted the service.. but still the time is 4 minutes behind...

i'm really stumped here... any more ideas???

---

### Post by Zill on 2009-08-01
LRT:  Two quick questions:

1)  You *have* got "ntpdate" as well as "ntp" installed on the server PC?

2)  Is the time shown on your server PC incorrect, or is it just the samba client PCs?

---

### Post by Shig on 2009-08-01
Perhaps try:
```
ntpdate time.windows.com
```The Microsoft time servers seem to allow for greater drift when doing initial syncronisation. Most NTP servers refuse to sycnronise if the drift between your PC and remote time is too great...

Please post the output of the above command once run.
Also please include the output of:

```
cat /etc/timezone
hwclock
date
```

---

