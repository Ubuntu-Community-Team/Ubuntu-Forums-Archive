---
title: "ntp server not listening"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by dninja on 2007-01-10
I've set up an ntp server on my server and tried to get it to act as a server for all other clients but clients can't connect to it.

The ntp.conf file contains:
```

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/
logfile /var/log/ntp.log

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org

restrict default kod notrap nomodify nopeer noquery
restrict 192.168.0.0 mask 255.255.255.0 nomodify notrap
restrict 0.pool.ntp.org mask 255.255.255.255 nomodify notrap noquery
restrict 1.pool.ntp.org mask 255.255.255.255 nomodify notrap noquery
restrict 2.pool.ntp.org mask 255.255.255.255 nomodify notrap noquery

restrict 127.0.0.1

server          127.127.1.0     # local clock
fudge           127.127.1.0 stratum 10
driftfile       /var/lib/ntp/drift
broadcastdelay  0.008
```

Looking in the log I see this:

```

Jan 10 12:44:22 myserv ntpd[26453]: Listening on interface lo, 127.0.0.1#123
Jan 10 12:44:22 myserv ntpd[26453]: Listening on interface eth0, 192.168.0.8#123
```

so it is listening, an nmap scan from a client confirms that udp port 123 is there and listening.

But when I try to use the server I get an error:
```
ntpdate myserv
10 Jan 12:44:47 ntpdate[4943]: no server suitable for synchronization found
```

Have I done something obvious wrong?

I have tried loads of different tutorials all of which generally say the same thing but not managed to get anywhere ](*,)

---

### Post by hogman23 on 2007-01-10
I'm having the same problem myself...somebody please help!!!

---

### Post by dninja on 2007-01-10
Fixed it!

I've removed the line:
```
restrict default kod notrap nomodify nopeer noquery
```
from the server and the client now connects to it.

Something to watchout for that I spotted while trying to fix this is dhcp servers, by default, overwrite the ntp.conf file. There are ways to disable this but I added the line:
```
option ntp-servers myserver;
```
to my dhcp conf file and so the ntp file still gets overwritten but with the correct information.

hogman23 - if you need any more info I'll give it. It just works so don't expect any explanations!

---

### Post by hogman23 on 2007-01-10
> **dninja said:**
> Fixed it!

I've removed the line:
```
restrict default kod notrap nomodify nopeer noquery
```
from the server and the client now connects to it.

Something to watchout for that I spotted while trying to fix this is dhcp servers, by default, overwrite the ntp.conf file. There are ways to disable this but I added the line:
```
option ntp-servers myserver;
```
to my dhcp conf file and so the ntp file still gets overwritten but with the correct information.

hogman23 - if you need any more info I'll give it. It just works so don't expect any explanations!

I removed that line, but my client still won't connect.  I am trying to connect using this command:
```
ntpdate servername 
```

I used nmap and it's listening on 123, but the client still says the same thing:

**10 Jan 16:26:48 ntpdate[19585]: no server suitable for synchronization found**

---

### Post by dninja on 2007-01-11
If you want copies of my config files or any other info PM me and I'll see what I can do.

---

### Post by hogman23 on 2007-01-11
Now it's working all of a sudden!!!!  I guess It needs time to sync up and I wasn't giving it a chance after I removed the line you said to remove.   Thanks for your help.

---

### Post by dninja on 2007-01-11
Brilliant, two happy users!
:)

---

### Post by shuaibe on 2007-07-09
make it three !!! thanks guys!

---

