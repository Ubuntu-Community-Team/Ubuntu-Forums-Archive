---
title: "NTP - Time and Date Question"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-29
How does my computer know what servers to check for the date and time sync?

Specifically, is there a config file that has the servers to connect to listed, can I change the list?

I'm getting what I feel is an excessive number of time and date sync updates (or attempts anyway) to too many servers and I do not even have auto time and date sync turned on.  None of these servers show up in a search of time servers through Google.

I am also not running an time/date update server service in Admin --> Services (unless it's under a cron job I cant see) 

thx

---

### Post by oldos2er on 2009-03-29
You need to create the file /etc/cron.daily/ntpdate . See [https://help.ubuntu.com/8.10/serverguide/C/NTP.html](https://help.ubuntu.com/8.10/serverguide/C/NTP.html)

---

### Post by mistypotato on 2009-03-29
thanks oldoser.

see, that's one of the things mystifying me....

I do not have a filed called /etc/ntp.conf anywhere on my computer (I searched).

So I cannot understand why my computer is trying to connect to more tha a dozen different time servers :confused:

And they are not ubuntu.com or any of the other servers I'm familiar with.

---

### Post by walkerk on 2009-03-29
i didn't even bother with cron. i have an autostart script in which i have the following:
```
sudo ntpdate time.gist.gov
```

obviously, /usr/sbin/ntpdate is configured in sudoers..

---

### Post by oldos2er on 2009-03-29
> **mistypotato said:**
> thanks oldoser.

see, that's one of the things mystifying me....

I do not have a filed called /etc/ntp.conf anywhere on my computer (I searched).

So I cannot understand why my computer is trying to connect to more tha a dozen different time servers :confused:

And they are not ubuntu.com or any of the other servers I'm familiar with.

 I have /etc/openntpd/ntpd.conf , but I am not even sure what openntpd is. I run a little script every once in a while too:
sudo ntpdate time.nist.gov

---

### Post by mistypotato on 2009-03-30
ok.

Well, I'm pretty darn sure there's some monkey business going on now.

My Firestarter log shows attempts by my server to contact foreign IP addresses all day.   There must be 100 different IP addresses now that have fortunately been blocked.  I have no idea where they're coming from.  I think tomorrow I'm going to use the "way back machine" (mondo recue) to restore my system back a month ago.  (unless someone posts with an explanation of course).

They are all UDP and all outbound on NTP service and all on port 123.

But I don't even have any ntp services set up so I'm beginning to believe I have a problem.

Is there any way this could be legitimate?

---

### Post by mistypotato on 2009-03-30
This is an update on this odd behavior.

I have discovered in the logs that a cron job is calling whatever process is making these outbound attempts to connect to hundreds of various servers.

update-motd to be specific is being called immediately before a batch of 5 outbound attempts are made.  This is done precisely hourly.

Obviously, my system has been compromised so a LLF and reinstall to an earlier mondo backup is in order.

Some suggest that sloppy administration caused this.  I'm of average to slightly above average server experience and the server sits behind a watchguard Firebox firewall.  So in addition to "sloppy" adminstration, it could also be a file or package thought to be trusted (from a source that appears reliable to my eyes, and I'm paranoid about such things), slipped by.

Or someone took advantage of an exploit before the patch came out.

A word of potential caution to anyone installing ubuntu server and needing a GUI.

It has been advised NOT to install a GUI with ubuntu server and this may be the key.  If you are going to need a server GUI, it may be better to install the non-server version of Ubuntu and then the server components needed.  I think that the server version was written such that it does not expect to have a GUI, and the process of adding one causes some security issues whereas the regular version expects the GUI and all the bells and whistles and therefore may be more "secure" when converted to a server than vice versa.

Hope this helps someone.

---

### Post by scorp123 on 2009-03-30
> **mistypotato said:**
>  Obviously, my system has been compromised How so?

Couldn't it just be that you installed some ntp package and that it is trying to reach default NTP servers in a pool? e.g. **0.pool.ntp.org**

Each country and region has their own pool sets, and there might be dozens of hosts in each pool. So if NTP was configured it may try to reach the pools in this order:

[INDENT]0.pool.ntp.org
1.pool.ntp.org
2.pool.ntp.org [/INDENT]

... and as there are dozens of servers in each pool, it might look like a bit odd.

But usually it should stop as soon as the NTP process gets a valid response from somewhere ... unless of course some badly configured firewall prevents any responses??

And thus the NTP process would go on and on and on trying to do what it was configured for: get time & date from somewhere. But no server is answering so it tries the next on its long pool list ....

You did not provide enough data and e.g. IP addresses, log samples, and so on. But based on your description I'd say that this is the scenario you are seeing, and not a remote attack from somewhere.

I at least am not aware of any method by which an attacker could gain remote access using the NTP protocol and UDP packets on port 123.

So before you destroy your server I'd suggest you invest a bit more time researching what IP blocks exactly are being contacted (there is a big big difference and whether or not your NTP process is talking to a legit NTP server pool or a nest of malware servers somewhere in China actually matters a lot!!) and if the firewall might be badly configured and by accident block things which it should not block ...

Just my 0.05€ as experienced Unix admin. ;)

---

### Post by scorp123 on 2009-03-30
> **mistypotato said:**
>  I do not have a filed called /etc/ntp.conf anywhere on my computer (I searched). That of course totally depends on what NTP package you installed. So why not check that instead?

```
sudo dpkg -l '*ntp*'
``` ... to this my server answers:
```
ii  ntp                                            1:4.2.4p0+dfsg-1ubuntu2.1                      Network Time Protocol daemon and utility programs
un  ntp-doc                                        <none>                                         (no description available)
un  ntp-refclock                                   <none>                                         (no description available)
un  ntp-server                                     <none>                                         (no description available)
un  ntp-simple                                     <none>                                         (no description available)
ii  ntpdate                                        1:4.2.4p0+dfsg-1ubuntu2.1                      client for setting system time from NTP servers
``` ... So I have two packages that are installed as can be seen by the "ii" marker.

Your result might be different. In any case it would be worth checking what config files are in those packages and where they are and what they are set to. To list the files inside a package you'd issue e.g. this command: ```
dpkg -L ntpdate
```

To this my system responds with:
```
/.
/etc
/etc/dhcp3
/etc/dhcp3/dhclient-exit-hooks.d
/etc/dhcp3/dhclient-exit-hooks.d/ntpdate
/etc/default
**/etc/default/ntpdate**
/etc/logcheck
/etc/logcheck/ignore.d.server
/etc/logcheck/ignore.d.server/ntpdate
/etc/network
/etc/network/if-up.d
/etc/network/if-up.d/ntpdate
/usr
/usr/sbin
/usr/sbin/ntpdate-debian
/usr/sbin/ntpdate
/usr/share
/usr/share/doc
/usr/share/doc/ntpdate
/usr/share/doc/ntpdate/README.Debian
/usr/share/doc/ntpdate/copyright
/usr/share/doc/ntpdate/NEWS.Debian.gz
/usr/share/doc/ntpdate/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/ntpdate.8.gz
/usr/share/man/man8/ntpdate-debian.8.gz
```

So the config file is here:
**/etc/default/ntpdate**

Again... your result might be different. But you should use some methodical way and analyse the causes for this behaviour step by step instead of jumping to any conclusions.

So depending on what the config file is you should take a look at it. Looking at my own file up there I can see these lines inside of it:
```
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# **Set to "yes" to take the server list from /etc/ntp.conf**, from package ntp,
# so you only have to keep it in one place.
**NTPDATE_USE_NTP_CONF=yes**

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="ntp.ubuntu.com"

# Additional options to pass to ntpdate
NTPOPTIONS=""
```

See the line I highlighted? So if this setting is active then it does not matter what is configured here in this file ... the actual server list is taken from this file: **/etc/ntp.conf**

And when we look at that file we can see these lines in my case:
```
...
server ntp.ubuntu.com
server swisstime.ethz.ch
server bernina.ethz.ch
...
```

So if I were not Swiss I might find it odd that my system tries to talk to some servers on a Swiss university (= ethz.ch is the "ETH Zurich").

What I'd suggest to you is that you please check ...
[LIST]
[*]which NTP packages are installed on your system?
[*]identify their config files
[*]check the configured settings
[*]compare the IP traffic you see with what is configured!
[/LIST]

If the destination servers are indeed NTP servers and they match the config files then I'd say your server was not compromised. If however your config files point to NTP servers in Europe and/or North America but your traffic is going to IP blocks assigned to some rather exotic places .. well, yes. That would be a different story.

---

### Post by mistypotato on 2009-03-30
Thanks scorp :)

Reading your posts carefully.  Incidentally, I removed "Cron" via synaptic and all other "cron" type services (anacron, logrotate, mlocate, popularity-contest) from ny system.

Surprisingly, the beat (UDP outbounds) goes on so again, I'm reading over your posts with a ftc.  

Thanks for your help :KS

---

### Post by kpatz on 2009-03-30
Type:
```

dpkg --get-selections '*ntp*'

```
What do you get?

If you have ntp installed (as opposed to ntpdate), it is a daemon which keeps your clock synchronized with a set of time servers.

If you see ntp installed, try:
```

ntpq -p

```
and see what you get.

---

### Post by scorp123 on 2009-03-30
> **mistypotato said:**
>  Surprisingly, the beat (UDP outbounds) goes on Did you check for running "ntp" type of programs and packages as I suggested?

Also, what do you get if you run this command:
```
sudo lsof -n -i -P
```

This should spit out the names of all programs that have open network connections somewhere somehow and also the name of the user account they are running under.

If I do that here I get this:
```
 > sudo lsof -n -i -P
COMMAND     PID  USER   FD   TYPE  DEVICE SIZE NODE NAME
avahi-dae  5221 avahi   14u  IPv4   16885       UDP *:5353 
avahi-dae  5221 avahi   15u  IPv4   16886       UDP *:42507 
sshd       5881  root    3u  IPv6 6383518       TCP *:22 (LISTEN)
sshd       5881  root    4u  IPv4 6383520       TCP *:22 (LISTEN)
Xvnc      14351   ron    0u  IPv6 2807116       TCP *:6001 (LISTEN)
Xvnc      14351   ron    1u  IPv4 2807117       TCP *:6001 (LISTEN)
Xvnc      14351   ron    4u  IPv4 2807121       TCP *:5901 (LISTEN)
[B]ntpd      18548   ntp   16u  IPv4 6062298       UDP *:123 
ntpd      18548   ntp   17u  IPv6 6062299       UDP *:123 
ntpd      18548   ntp   20u  IPv4 6062305       UDP 127.0.0.1:123 
ntpd      18548   ntp   21u  IPv4 6062306       UDP 192.168.1.210:123 
[/B]cupsd     22197  root    0u  IPv4 5648282       TCP 127.0.0.1:631 (LISTEN)
cupsd     22197  root    4u  IPv4 5648286       UDP *:631 
dhclient  25259  root    5u  IPv4 5627485       UDP *:68 
vino-serv 31436   eve   16u  IPv6 4874636       TCP *:5900 (LISTEN)

```
As you can see the **ntpd** = NTP daemon gets listed a few times which would be normal as the package "**ntp**" is installed and running. So it's supposed to be listed here.

What would be odd is if a totally unrelated binary would get listed, e.g. something weird like this:
```
firefox      18548   root   17u  IPv6 6062299       UDP *:123
``` ... this example is fabricated, but what it would mean is that there would seem to be a Firefox process running with full "root" super-user priviledges (bad, bad, bad, baaddd!! NEVER ever do that!) and it is listening for incoming UDP traffic on port 123 .....  Now something like that would be extremely weird and an indication that I'd be running a Trojaned version of Firefox ....

You don't happen to see something like that, do you?

Also worth checking is what "netstat" says about your connections and where they are going and why ... If I do that here I get this:
```
> sudo netstat -tuan | more
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.210:54700     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:56992     212.243.221.249:80      ESTABLISHED
tcp        0      0 192.168.1.210:60486     212.243.221.247:80      ESTABLISHED
tcp        0      0 192.168.1.210:41401     91.198.174.3:80         TIME_WAIT  
tcp        0      0 192.168.1.210:60485     212.243.221.247:80      ESTABLISHED
tcp        0      0 192.168.1.210:41403     91.198.174.3:80         TIME_WAIT  
tcp        0      0 192.168.1.210:52919     72.14.221.191:80        TIME_WAIT  
tcp        0      0 192.168.1.210:49399     72.14.221.104:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54699     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:55480     72.14.221.99:80         TIME_WAIT  
tcp        0      0 192.168.1.210:37934     72.14.221.118:80        ESTABLISHED
tcp        0      0 192.168.1.210:59628     74.125.43.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:52920     72.14.221.191:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54696     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:59621     74.125.43.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:59626     74.125.43.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:60488     212.243.221.247:80      ESTABLISHED
tcp        0      0 192.168.1.210:60489     212.243.221.247:80      ESTABLISHED
tcp        0      0 192.168.1.210:59625     74.125.43.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54697     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:52918     72.14.221.191:80        TIME_WAIT  
tcp        0      0 192.168.1.210:33935     208.77.137.146:80       ESTABLISHED
tcp        0      0 192.168.1.210:59624     74.125.43.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54698     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:59622     74.125.43.103:80        ESTABLISHED
tcp        0      0 192.168.1.210:54702     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:60487     212.243.221.247:80      ESTABLISHED
tcp        0      0 192.168.1.210:52927     72.14.221.191:80        ESTABLISHED
tcp        0      0 192.168.1.210:55491     72.14.221.99:80         TIME_WAIT  
tcp        0      0 192.168.1.210:49404     72.14.221.104:80        TIME_WAIT  
tcp        0      0 192.168.1.210:41856     212.58.253.68:80        TIME_WAIT  
tcp        0      0 192.168.1.210:45919     72.14.221.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54701     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:37925     72.14.221.118:80        ESTABLISHED
tcp        0      0 192.168.1.210:59623     74.125.43.103:80        ESTABLISHED
tcp        0      0 192.168.1.210:52922     72.14.221.191:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54705     91.198.174.2:80         TIME_WAIT  
tcp        0      0 192.168.1.210:41855     212.58.253.68:80        TIME_WAIT  
tcp        0      0 192.168.1.210:49427     72.14.221.104:80        ESTABLISHED
tcp        0      0 192.168.1.210:52921     72.14.221.191:80        TIME_WAIT  
tcp        0      0 192.168.1.210:37927     72.14.221.118:80        ESTABLISHED
tcp        0      0 192.168.1.210:59619     74.125.43.103:80        TIME_WAIT  
tcp        0      0 192.168.1.210:54703     91.198.174.2:80         TIME_WAIT  
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::6001                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
udp        0      0 0.0.0.0:42507           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*
```

Those stars "*" mean that a program is waiting for incoming connections. But more interesting is the list of already established connections. If you do a "nslookup" on those IP's you will see where the connections are going to and if this is legit traffic or not.

"91.198.174.2" for example belongs to wikimedia.org ... so we can assume that this originates from me browsing something in Wikipedia. So that traffic is OK.

When I do a lookup on "212.243.221.249" nslookup can't find an entry:
```
> nslookup 212.243.221.249
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find 249.221.243.212.in-addr.arpa.: NXDOMAIN
```

So those guys are either hiding something or they did not care to configure their DNS properly. We can still find out who they are via the **whois** program:
```
 > whois 212.243.221.249
% This is the RIPE Whois query server #1.
% The objects are in RPSL format.
%
% Rights restricted by copyright.
% See http://www.ripe.net/db/copyright.html

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '212.243.221.194 - 212.243.221.255'

inetnum:        212.243.221.194 - 212.243.221.255
netname:        AKAMAI-NET
descr:          Akamai Technologies Inc.
descr:          02139 Cambridge, MA 02139
country:        CH
admin-c:        CK7138-RIPE
tech-c:         CK7138-RIPE
status:         ASSIGNED PA
mnt-by:	        CH-UNISOURCE-MNT
source:	        RIPE # Filtered

person:       Christian Klacko
address:      Akamai Technologies, Cambridge
address:      500 Technology Square
address:      02139 Cambridge, MA
address:      USA
phone:        +1 6172503046
fax-no:       +1 6172503001
e-mail:       cklacko@akamai.com
nic-hdl:      CK7138-RIPE
mnt-by:       UUNET-P
source:       RIPE # Filtered

% Information related to '212.243.0.0/16AS3303'

route:        212.243.0.0/16
descr:        Swisscom AG
descr:        Provider
origin:       AS3303
mnt-by:       CH-UNISOURCE-MNT
source:       RIPE # Filtered

% Information related to '212.243.221.0/24AS3303'

route:          212.243.221.0/24
descr:          Swisscom AG
descr:          Colo
origin:         AS3303
mnt-by:         CH-UNISOURCE-MNT
source:         RIPE # Filtered
```

So this range belongs to Swisscom ... who happen to be my ISP. So this traffic too is legit (I was accessing a few of their web pages just a few minutes ago).

So I'd suggest you too do something like this and systemathically go through the list of IP's your installation is connecting to and check out who and what they are.

---

### Post by mistypotato on 2009-03-30
I got a good bit more when I typed that command....

sudo lsof -n -i -P
 
COMMAND     PID     USER   FD   TYPE DEVICE SIZE NODE NAME
avahi-dae  4442    avahi   14u  IPv4  14742       UDP *:5353 
avahi-dae  4442    avahi   15u  IPv4  14743       UDP *:49817 
named      4470     bind   20u  IPv4  14799       TCP 127.0.0.1:53 (LISTEN)
named      4470     bind   21u  IPv4  14801       TCP 192.168.4.12:53 (LISTEN)
named      4470     bind   22u  IPv4  14803       TCP 127.0.0.1:953 (LISTEN)
named      4470     bind  512u  IPv4  14798       UDP 127.0.0.1:53 
named      4470     bind  513u  IPv4  14800       UDP 192.168.4.12:53 
named      4470     bind  514u  IPv4  14802       UDP *:37834 
sshd       4496     root    3u  IPv4  14845       TCP 192.168.4.12:51500 (LISTEN)
mysqld     4597    mysql   10u  IPv4  14970       TCP 127.0.0.1:3306 (LISTEN)
cupsd      4872     root    2u  IPv4 787592       TCP 127.0.0.1:631 (LISTEN)
vsftpd     5155     root    3u  IPv4  16856       TCP *:21 (LISTEN)
java       6444  mpotato   23u  IPv6  53073       TCP 127.0.0.1:34480->127.0.0.1:53567 (ESTABLISHED)
miniserv.  6786     root    5u  IPv4  25657       TCP *:10000 (LISTEN)
miniserv.  6786     root    6u  IPv4  25658       UDP *:10000 
apache2    7081 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2    7081 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2    7081 www-data   40u  IPv4 938928       TCP 127.0.0.1:53378->127.0.0.1:6800 (CLOSE_WAIT)
apache2    7081 www-data   41u  IPv4 917124       TCP 127.0.0.1:60406->127.0.0.1:6800 (CLOSE_WAIT)
java       8940  mpotato  102u  IPv6  53070       TCP *:55415 (LISTEN)
java       8940  mpotato  106u  IPv6  53072       TCP 127.0.0.1:53567->127.0.0.1:34480 (ESTABLISHED)
java       8940  mpotato  110u  IPv6  53085       TCP 127.0.0.1:6800 (LISTEN)
java       8940  mpotato  111u  IPv6  53086       TCP *:8600 (LISTEN)
apache2   13594 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   13594 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   13594 www-data   40u  IPv4 938256       TCP 127.0.0.1:59544->127.0.0.1:6800 (CLOSE_WAIT)
apache2   13594 www-data   41u  IPv4 924492       TCP 127.0.0.1:43989->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15218 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   15218 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   15218 www-data   40u  IPv4 937284       TCP 127.0.0.1:35250->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15218 www-data   41u  IPv4 924640       TCP 127.0.0.1:43996->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15227 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   15227 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   15227 www-data   40u  IPv4 939675       TCP 127.0.0.1:36013->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15227 www-data   41u  IPv4 898530       TCP 127.0.0.1:46508->127.0.0.1:6800 (CLOSE_WAIT)
apache2   18317     root    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   18317     root    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   22673 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   22673 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   22673 www-data   40u  IPv4 938340       TCP 127.0.0.1:59545->127.0.0.1:6800 (CLOSE_WAIT)
apache2   22673 www-data   41u  IPv4 898330       TCP 127.0.0.1:34644->127.0.0.1:6800 (CLOSE_WAIT)
apache2   23606 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   23606 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   23606 www-data   40u  IPv4 938369       TCP 127.0.0.1:59546->127.0.0.1:6800 (CLOSE_WAIT)
apache2   23846 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   23846 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   23846 www-data   40u  IPv4 937731       TCP 127.0.0.1:49656->127.0.0.1:6800 (CLOSE_WAIT)
apache2   23846 www-data   41u  IPv4 898053       TCP 127.0.0.1:34630->127.0.0.1:6800 (CLOSE_WAIT)
apache2   23848 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   23848 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   23848 www-data   40u  IPv4 938608       TCP 127.0.0.1:59547->127.0.0.1:6800 (CLOSE_WAIT)
apache2   23848 www-data   41u  IPv4 915846       TCP 127.0.0.1:39102->127.0.0.1:6800 (CLOSE_WAIT)
apache2   29123 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   29123 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   29123 www-data   40u  IPv4 938921       TCP 127.0.0.1:53377->127.0.0.1:6800 (CLOSE_WAIT)
apache2   29123 www-data   41u  IPv4 910854       TCP 127.0.0.1:41813->127.0.0.1:6800 (CLOSE_WAIT)
apache2   30139 www-data    3u  IPv4 462763       TCP *:80 (LISTEN)
apache2   30139 www-data    4u  IPv4 462765       TCP *:443 (LISTEN)
apache2   30139 www-data   40u  IPv4 938918       TCP 127.0.0.1:53376->127.0.0.1:6800 (CLOSE_WAIT)
apache2   30139 www-data   41u  IPv4 908025       TCP 127.0.0.1:52909->127.0.0.1:6800 (CLOSE_WAIT)



**netstat...........**


mpotato@PotatoServer:~$ sudo netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      0 localhost:43989         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:41813         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:53378         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:36013         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:43996         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:52909         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:59546         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:46508         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:53376         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:59544         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:34630         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:34644         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:59545         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:60406         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:49656         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:39102         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:59547         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:53377         localhost:6800          CLOSE_WAIT 
tcp        1      0 localhost:40501         localhost:6800          CLOSE_WAIT 
tcp6       0      0 localhost:34480         localhost:53567         ESTABLISHED
tcp6       0      0 localhost:53567         localhost:34480         ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    5432     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    5618     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    17368    @/org/freedesktop/hal/udev_event
unix  5      [ ]         DGRAM                    859105   /dev/log
unix  3      [ ]         STREAM     CONNECTED     942737   /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     942736   
unix  3      [ ]         STREAM     CONNECTED     942722   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     942721   
unix  3      [ ]         STREAM     CONNECTED     942618   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     942617   
unix  3      [ ]         STREAM     CONNECTED     942610   /tmp/orbit-mpotato/linc-15aa-0-63376be360f2f
unix  3      [ ]         STREAM     CONNECTED     942609   
unix  3      [ ]         STREAM     CONNECTED     942606   /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     942605   
unix  3      [ ]         STREAM     CONNECTED     942604   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     942603   
unix  3      [ ]         STREAM     CONNECTED     942602   /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     942601   
unix  3      [ ]         STREAM     CONNECTED     942597   /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     942596   
unix  3      [ ]         STREAM     CONNECTED     939578   /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     939577   
unix  3      [ ]         STREAM     CONNECTED     939541   
unix  3      [ ]         STREAM     CONNECTED     939540   
unix  3      [ ]         STREAM     CONNECTED     939534   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     939533   
unix  3      [ ]         STREAM     CONNECTED     939532   /tmp/orbit-mpotato/linc-12c4-0-2694cf2f28e97
unix  3      [ ]         STREAM     CONNECTED     939531   
unix  3      [ ]         STREAM     CONNECTED     939530   /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     939529   
unix  3      [ ]         STREAM     CONNECTED     939528   /tmp/orbit-mpotato/linc-12c4-0-2694cf2f28e97
unix  3      [ ]         STREAM     CONNECTED     939527   
unix  3      [ ]         STREAM     CONNECTED     939524   /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     939523   
unix  3      [ ]         STREAM     CONNECTED     939522   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     939521   
unix  3      [ ]         STREAM     CONNECTED     939520   /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     939519   
unix  3      [ ]         STREAM     CONNECTED     939515   /tmp/.X11-unix/X0
unix  7      [ ]         STREAM     CONNECTED     939514   
unix  3      [ ]         STREAM     CONNECTED     895966   /tmp/orbit-root/linc-6993-0-2e85f278d52ea
unix  3      [ ]         STREAM     CONNECTED     895965   
unix  3      [ ]         STREAM     CONNECTED     895962   /tmp/orbit-root/linc-2bfa-0-4dabd7034ff97
unix  3      [ ]         STREAM     CONNECTED     895961   
unix  3      [ ]         STREAM     CONNECTED     895960   @/tmp/dbus-cNvhm8fk6t
unix  3      [ ]         STREAM     CONNECTED     895959   
unix  3      [ ]         STREAM     CONNECTED     895948   /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     895947   
unix  3      [ ]         STREAM     CONNECTED     895911   /tmp/orbit-mpotato/linc-6992-0-772575846104
unix  3      [ ]         STREAM     CONNECTED     895910   
unix  3      [ ]         STREAM     CONNECTED     895907   /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     895906   
unix  3      [ ]         STREAM     CONNECTED     895902   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     895901   
unix  4      [ ]         STREAM     CONNECTED     895900   /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     895899   
unix  2      [ ]         DGRAM                    886295   
unix  2      [ ]         DGRAM                    869830   
unix  2      [ ]         DGRAM                    859187   
unix  3      [ ]         STREAM     CONNECTED     485792   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     485791   
unix  3      [ ]         STREAM     CONNECTED     485790   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     485789   
unix  3      [ ]         STREAM     CONNECTED     485788   /tmp/orbit-mpotato/linc-545e-0-24e76650ef6d9
unix  3      [ ]         STREAM     CONNECTED     485787   
unix  3      [ ]         STREAM     CONNECTED     485784   /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     485783   
unix  3      [ ]         STREAM     CONNECTED     485780   @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     485779   
unix  3      [ ]         STREAM     CONNECTED     485776   /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     485775   
unix  3      [ ]         STREAM     CONNECTED     485773   /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     485772   
unix  3      [ ]         STREAM     CONNECTED     370471   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     370470   
unix  2      [ ]         STREAM     CONNECTED     99919    
unix  3      [ ]         STREAM     CONNECTED     77899    /tmp/orbit-root/linc-2ef1-0-5a52c22624d7e
unix  3      [ ]         STREAM     CONNECTED     77898    
unix  3      [ ]         STREAM     CONNECTED     77895    /tmp/orbit-root/linc-2bfa-0-4dabd7034ff97
unix  3      [ ]         STREAM     CONNECTED     77894    
unix  3      [ ]         STREAM     CONNECTED     77893    @/tmp/dbus-cNvhm8fk6t
unix  3      [ ]         STREAM     CONNECTED     77892    
unix  3      [ ]         STREAM     CONNECTED     77882    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     77881    
unix  3      [ ]         STREAM     CONNECTED     77851    /tmp/orbit-mpotato/linc-2ef0-0-4be0d7cfcf11b
unix  3      [ ]         STREAM     CONNECTED     77850    
unix  3      [ ]         STREAM     CONNECTED     77847    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     77846    
unix  3      [ ]         STREAM     CONNECTED     77842    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     77841    
unix  8      [ ]         STREAM     CONNECTED     77840    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     77839    
unix  3      [ ]         STREAM     CONNECTED     75656    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     75655    
unix  3      [ ]         STREAM     CONNECTED     75653    @/tmp/dbus-cNvhm8fk6t
unix  3      [ ]         STREAM     CONNECTED     75652    
unix  3      [ ]         STREAM     CONNECTED     75638    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     75637    
unix  3      [ ]         STREAM     CONNECTED     75636    
unix  3      [ ]         STREAM     CONNECTED     75635    
unix  6      [ ]         STREAM     CONNECTED     75622    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     75621    
unix  2      [ ]         STREAM     CONNECTED     71745    
unix  366    [ ]         STREAM     CONNECTED     71742    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     71741    
unix  3      [ ]         STREAM     CONNECTED     71729    /tmp/.X11-unix/X0
unix  4      [ ]         STREAM     CONNECTED     71728    
unix  3      [ ]         STREAM     CONNECTED     70308    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     70307    
unix  3      [ ]         STREAM     CONNECTED     70233    /tmp/orbit-mpotato/linc-295e-0-4bf3655b271c6
unix  4      [ ]         STREAM     CONNECTED     70232    
unix  3      [ ]         STREAM     CONNECTED     70229    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     70228    
unix  3      [ ]         STREAM     CONNECTED     70224    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     70223    
unix  362    [ ]         STREAM     CONNECTED     70222    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     70221    
unix  3      [ ]         STREAM     CONNECTED     33003    @/dbus-vfs-daemon/socket-HQKVfVks
unix  3      [ ]         STREAM     CONNECTED     33002    
unix  3      [ ]         STREAM     CONNECTED     33004    @/dbus-vfs-daemon/socket-28SgvCgl
unix  3      [ ]         STREAM     CONNECTED     33001    
unix  3      [ ]         STREAM     CONNECTED     32993    @/dbus-vfs-daemon/socket-pAEJHveL
unix  3      [ ]         STREAM     CONNECTED     32992    
unix  3      [ ]         STREAM     CONNECTED     32994    @/dbus-vfs-daemon/socket-t9e8DshT
unix  3      [ ]         STREAM     CONNECTED     32991    
unix  3      [ ]         STREAM     CONNECTED     32988    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     32987    
unix  3      [ ]         STREAM     CONNECTED     32986    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     32985    
unix  3      [ ]         STREAM     CONNECTED     32983    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     32982    
unix  3      [ ]         STREAM     CONNECTED     24389    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     24388    
unix  3      [ ]         STREAM     CONNECTED     24086    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     24085    
unix  3      [ ]         STREAM     CONNECTED     23635    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     23634    
unix  3      [ ]         STREAM     CONNECTED     23630    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     23629    
unix  3      [ ]         STREAM     CONNECTED     23621    @/dbus-vfs-daemon/socket-RGmWa3tV
unix  3      [ ]         STREAM     CONNECTED     23620    
unix  3      [ ]         STREAM     CONNECTED     23622    @/dbus-vfs-daemon/socket-9LBN4LzT
unix  3      [ ]         STREAM     CONNECTED     23619    
unix  3      [ ]         STREAM     CONNECTED     23614    @/dbus-vfs-daemon/socket-ZBeLtMLG
unix  3      [ ]         STREAM     CONNECTED     23613    
unix  3      [ ]         STREAM     CONNECTED     23612    @/dbus-vfs-daemon/socket-uU2dnvSR
unix  3      [ ]         STREAM     CONNECTED     23611    
unix  3      [ ]         STREAM     CONNECTED     23608    /tmp/orbit-mpotato/linc-18ed-0-43575217bdf04
unix  3      [ ]         STREAM     CONNECTED     23607    
unix  3      [ ]         STREAM     CONNECTED     23606    /tmp/orbit-mpotato/linc-1912-0-17ebdf88e85de
unix  3      [ ]         STREAM     CONNECTED     23605    
unix  3      [ ]         STREAM     CONNECTED     23603    @/dbus-vfs-daemon/socket-9yoXV8nD
unix  3      [ ]         STREAM     CONNECTED     23602    
unix  3      [ ]         STREAM     CONNECTED     23604    @/dbus-vfs-daemon/socket-Wan0MCDk
unix  3      [ ]         STREAM     CONNECTED     23601    
unix  3      [ ]         STREAM     CONNECTED     23591    @/dbus-vfs-daemon/socket-atxLk6kl
unix  3      [ ]         STREAM     CONNECTED     23590    
unix  3      [ ]         STREAM     CONNECTED     23592    @/dbus-vfs-daemon/socket-OVP2l0UM
unix  3      [ ]         STREAM     CONNECTED     23589    
unix  3      [ ]         STREAM     CONNECTED     23579    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23578    
unix  3      [ ]         STREAM     CONNECTED     23343    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23342    
unix  3      [ ]         STREAM     CONNECTED     23333    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     23332    
unix  3      [ ]         STREAM     CONNECTED     23331    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23330    
unix  3      [ ]         STREAM     CONNECTED     23328    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     23327    
unix  3      [ ]         STREAM     CONNECTED     23329    /tmp/orbit-mpotato/linc-18ed-0-43575217bdf04
unix  3      [ ]         STREAM     CONNECTED     23326    
unix  3      [ ]         STREAM     CONNECTED     23325    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     23324    
unix  3      [ ]         STREAM     CONNECTED     23323    /tmp/orbit-mpotato/linc-18ed-0-43575217bdf04
unix  3      [ ]         STREAM     CONNECTED     23322    
unix  3      [ ]         STREAM     CONNECTED     23320    /tmp/orbit-mpotato/linc-1922-0-73ae14ca51ef4
unix  3      [ ]         STREAM     CONNECTED     23319    
unix  3      [ ]         STREAM     CONNECTED     23318    /tmp/orbit-mpotato/linc-191f-0-73ae14ca95bc8
unix  3      [ ]         STREAM     CONNECTED     23317    
unix  3      [ ]         STREAM     CONNECTED     23293    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23292    
unix  3      [ ]         STREAM     CONNECTED     23291    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23290    
unix  3      [ ]         STREAM     CONNECTED     23289    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23288    
unix  3      [ ]         STREAM     CONNECTED     23287    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23286    
unix  3      [ ]         STREAM     CONNECTED     23266    /tmp/orbit-mpotato/linc-1929-0-60e70ef72f46e
unix  3      [ ]         STREAM     CONNECTED     23265    
unix  3      [ ]         STREAM     CONNECTED     23264    /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     23263    
unix  3      [ ]         STREAM     CONNECTED     23254    /tmp/orbit-mpotato/linc-1929-0-60e70ef72f46e
unix  3      [ ]         STREAM     CONNECTED     23253    
unix  3      [ ]         STREAM     CONNECTED     23250    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     23249    
unix  3      [ ]         STREAM     CONNECTED     23248    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23247    
unix  3      [ ]         STREAM     CONNECTED     23246    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     23245    
unix  3      [ ]         STREAM     CONNECTED     23241    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23240    
unix  3      [ ]         STREAM     CONNECTED     23228    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     23227    
unix  3      [ ]         STREAM     CONNECTED     23205    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23204    
unix  3      [ ]         STREAM     CONNECTED     23203    /tmp/orbit-mpotato/linc-192d-0-215f3d6e97f8
unix  3      [ ]         STREAM     CONNECTED     23202    
unix  3      [ ]         STREAM     CONNECTED     23199    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     23198    
unix  3      [ ]         STREAM     CONNECTED     23194    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23193    
unix  3      [ ]         STREAM     CONNECTED     23135    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23134    
unix  3      [ ]         STREAM     CONNECTED     23130    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23129    
unix  3      [ ]         STREAM     CONNECTED     23127    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23126    
unix  3      [ ]         STREAM     CONNECTED     23125    /tmp/orbit-mpotato/linc-1926-0-4a2175e8b53c
unix  3      [ ]         STREAM     CONNECTED     23124    
unix  3      [ ]         STREAM     CONNECTED     23121    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     23120    
unix  3      [ ]         STREAM     CONNECTED     23119    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23118    
unix  3      [ ]         STREAM     CONNECTED     23117    /tmp/orbit-mpotato/linc-1928-0-4a2175e85da9
unix  3      [ ]         STREAM     CONNECTED     23116    
unix  3      [ ]         STREAM     CONNECTED     23113    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     23112    
unix  3      [ ]         STREAM     CONNECTED     23111    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     23110    
unix  3      [ ]         STREAM     CONNECTED     23058    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23057    
unix  3      [ ]         STREAM     CONNECTED     23109    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     23108    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     22963    
unix  3      [ ]         STREAM     CONNECTED     22959    
unix  3      [ ]         STREAM     CONNECTED     22955    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22954    
unix  3      [ ]         STREAM     CONNECTED     22953    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22952    
unix  3      [ ]         STREAM     CONNECTED     22753    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22752    
unix  3      [ ]         STREAM     CONNECTED     22751    /tmp/orbit-mpotato/linc-191f-0-73ae14ca95bc8
unix  3      [ ]         STREAM     CONNECTED     22750    
unix  3      [ ]         STREAM     CONNECTED     22749    /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     22748    
unix  3      [ ]         STREAM     CONNECTED     22747    /tmp/orbit-mpotato/linc-191f-0-73ae14ca95bc8
unix  3      [ ]         STREAM     CONNECTED     22746    
unix  3      [ ]         STREAM     CONNECTED     22743    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22742    
unix  3      [ ]         STREAM     CONNECTED     22741    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22740    
unix  3      [ ]         STREAM     CONNECTED     22736    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22735    
unix  3      [ ]         STREAM     CONNECTED     22729    /tmp/orbit-mpotato/linc-1922-0-73ae14ca51ef4
unix  3      [ ]         STREAM     CONNECTED     22728    
unix  3      [ ]         STREAM     CONNECTED     22727    /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     22726    
unix  3      [ ]         STREAM     CONNECTED     22725    /tmp/orbit-mpotato/linc-1922-0-73ae14ca51ef4
unix  3      [ ]         STREAM     CONNECTED     22724    
unix  3      [ ]         STREAM     CONNECTED     22721    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22720    
unix  3      [ ]         STREAM     CONNECTED     22719    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22718    
unix  3      [ ]         STREAM     CONNECTED     22714    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22713    
unix  3      [ ]         STREAM     CONNECTED     22630    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22629    
unix  3      [ ]         STREAM     CONNECTED     22621    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22620    
unix  3      [ ]         STREAM     CONNECTED     22580    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22579    
unix  3      [ ]         STREAM     CONNECTED     22578    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22577    
unix  3      [ ]         STREAM     CONNECTED     22576    /tmp/orbit-mpotato/linc-1912-0-17ebdf88e85de
unix  3      [ ]         STREAM     CONNECTED     22575    
unix  3      [ ]         STREAM     CONNECTED     22574    /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     22573    
unix  3      [ ]         STREAM     CONNECTED     22569    @/dbus-vfs-daemon/socket-2H8eDNuc
unix  3      [ ]         STREAM     CONNECTED     22568    
unix  3      [ ]         STREAM     CONNECTED     22570    @/dbus-vfs-daemon/socket-vaP031pl
unix  3      [ ]         STREAM     CONNECTED     22567    
unix  3      [ ]         STREAM     CONNECTED     22560    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22559    
unix  3      [ ]         STREAM     CONNECTED     22538    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22537    
unix  3      [ ]         STREAM     CONNECTED     22536    /tmp/orbit-mpotato/linc-1912-0-17ebdf88e85de
unix  3      [ ]         STREAM     CONNECTED     22535    
unix  3      [ ]         STREAM     CONNECTED     22532    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22531    
unix  3      [ ]         STREAM     CONNECTED     22530    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22529    
unix  3      [ ]         STREAM     CONNECTED     22524    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22523    
unix  3      [ ]         STREAM     CONNECTED     22520    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22519    
unix  3      [ ]         STREAM     CONNECTED     22484    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22483    
unix  3      [ ]         STREAM     CONNECTED     22479    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22478    
unix  3      [ ]         STREAM     CONNECTED     22477    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22476    
unix  3      [ ]         STREAM     CONNECTED     22475    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22474    
unix  3      [ ]         STREAM     CONNECTED     22466    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22465    
unix  3      [ ]         STREAM     CONNECTED     22464    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22463    
unix  3      [ ]         STREAM     CONNECTED     22462    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22461    
unix  3      [ ]         STREAM     CONNECTED     22453    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22452    
unix  3      [ ]         STREAM     CONNECTED     22451    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22450    
unix  3      [ ]         STREAM     CONNECTED     22449    /tmp/orbit-mpotato/linc-18cc-0-571d2389a913
unix  3      [ ]         STREAM     CONNECTED     22448    
unix  3      [ ]         STREAM     CONNECTED     22445    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22444    
unix  3      [ ]         STREAM     CONNECTED     22438    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22437    
unix  3      [ ]         STREAM     CONNECTED     22405    /tmp/orbit-mpotato/linc-18ed-0-43575217bdf04
unix  3      [ ]         STREAM     CONNECTED     22404    
unix  3      [ ]         STREAM     CONNECTED     22402    /tmp/orbit-mpotato/linc-18f7-0-71b1b71f38890
unix  3      [ ]         STREAM     CONNECTED     22401    
unix  3      [ ]         STREAM     CONNECTED     22400    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22399    
unix  3      [ ]         STREAM     CONNECTED     22403    /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     22398    
unix  3      [ ]         STREAM     CONNECTED     22397    /tmp/orbit-mpotato/linc-18fa-0-2750ef21a8e84
unix  3      [ ]         STREAM     CONNECTED     22396    
unix  3      [ ]         STREAM     CONNECTED     22390    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22389    
unix  3      [ ]         STREAM     CONNECTED     22388    /tmp/orbit-mpotato/linc-1904-0-103bdb5687bf0
unix  3      [ ]         STREAM     CONNECTED     22387    
unix  3      [ ]         STREAM     CONNECTED     22384    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22383    
unix  3      [ ]         STREAM     CONNECTED     22379    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22378    
unix  3      [ ]         STREAM     CONNECTED     22377    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22376    
unix  3      [ ]         STREAM     CONNECTED     22373    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22372    
unix  3      [ ]         STREAM     CONNECTED     22297    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22296    
unix  3      [ ]         STREAM     CONNECTED     22287    /tmp/orbit-mpotato/linc-18f7-0-71b1b71f38890
unix  3      [ ]         STREAM     CONNECTED     22286    
unix  3      [ ]         STREAM     CONNECTED     22283    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22282    
unix  3      [ ]         STREAM     CONNECTED     22281    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22280    
unix  3      [ ]         STREAM     CONNECTED     22279    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     22278    
unix  3      [ ]         STREAM     CONNECTED     22274    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22273    
unix  3      [ ]         STREAM     CONNECTED     22226    /tmp/orbit-mpotato/linc-18ed-0-43575217bdf04
unix  3      [ ]         STREAM     CONNECTED     22225    
unix  3      [ ]         STREAM     CONNECTED     22222    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22221    
unix  3      [ ]         STREAM     CONNECTED     22220    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22219    
unix  3      [ ]         STREAM     CONNECTED     22164    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22163    
unix  3      [ ]         STREAM     CONNECTED     22103    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     22102    
unix  3      [ ]         STREAM     CONNECTED     22101    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22100    
unix  3      [ ]         STREAM     CONNECTED     22096    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22095    
unix  3      [ ]         STREAM     CONNECTED     22073    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22072    
unix  3      [ ]         STREAM     CONNECTED     22042    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     22041    
unix  3      [ ]         STREAM     CONNECTED     22015    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22014    
unix  3      [ ]         STREAM     CONNECTED     22007    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     22006    
unix  3      [ ]         STREAM     CONNECTED     22005    /tmp/orbit-mpotato/linc-18d4-0-4f622dbfd431d
unix  3      [ ]         STREAM     CONNECTED     22004    
unix  3      [ ]         STREAM     CONNECTED     22001    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     22000    
unix  3      [ ]         STREAM     CONNECTED     21972    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     21971    
unix  3      [ ]         STREAM     CONNECTED     21970    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21969    
unix  3      [ ]         STREAM     CONNECTED     21894    /tmp/orbit-mpotato/linc-18d3-0-548bad9a20567
unix  3      [ ]         STREAM     CONNECTED     21893    
unix  3      [ ]         STREAM     CONNECTED     21890    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     21889    
unix  3      [ ]         STREAM     CONNECTED     21854    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     21853    
unix  3      [ ]         STREAM     CONNECTED     21852    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21851    
unix  3      [ ]         STREAM     CONNECTED     21848    /tmp/.ICE-unix/6215
unix  3      [ ]         STREAM     CONNECTED     21847    
unix  3      [ ]         STREAM     CONNECTED     21842    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     21841    
unix  2      [ ]         DGRAM                    21750    
unix  3      [ ]         STREAM     CONNECTED     21749    /tmp/orbit-mpotato/linc-1847-0-457145df2c3dc
unix  3      [ ]         STREAM     CONNECTED     21748    
unix  3      [ ]         STREAM     CONNECTED     21745    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     21744    
unix  3      [ ]         STREAM     CONNECTED     21708    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     21707    
unix  3      [ ]         STREAM     CONNECTED     21705    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21704    
unix  3      [ ]         STREAM     CONNECTED     21680    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21679    
unix  3      [ ]         STREAM     CONNECTED     21672    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21671    
unix  3      [ ]         STREAM     CONNECTED     21670    /tmp/orbit-mpotato/linc-18c4-0-27c9a445ba847
unix  3      [ ]         STREAM     CONNECTED     21669    
unix  3      [ ]         STREAM     CONNECTED     21666    /tmp/orbit-mpotato/linc-18c6-0-659b271c8f8df
unix  3      [ ]         STREAM     CONNECTED     21665    
unix  3      [ ]         STREAM     CONNECTED     21659    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21658    
unix  3      [ ]         STREAM     CONNECTED     21408    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     21407    
unix  3      [ ]         STREAM     CONNECTED     21394    @/tmp/dbus-zkOt8bEDFQ
unix  3      [ ]         STREAM     CONNECTED     21393    
unix  3      [ ]         STREAM     CONNECTED     21351    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21350    
unix  3      [ ]         STREAM     CONNECTED     21326    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21325    
unix  3      [ ]         STREAM     CONNECTED     21321    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21320    
unix  3      [ ]         STREAM     CONNECTED     21319    
unix  3      [ ]         STREAM     CONNECTED     21318    
unix  8      [ ]         STREAM     CONNECTED     21305    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21304    
unix  3      [ ]         STREAM     CONNECTED     20678    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20677    
unix  2      [ ]         DGRAM                    20670    
unix  3      [ ]         STREAM     CONNECTED     20647    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20646    
unix  3      [ ]         STREAM     CONNECTED     19374    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19373    
unix  6      [ ]         STREAM     CONNECTED     19635    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19372    
unix  3      [ ]         STREAM     CONNECTED     18690    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     18689    
unix  3      [ ]         STREAM     CONNECTED     18662    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18661    
unix  2      [ ]         DGRAM                    18474    
unix  3      [ ]         STREAM     CONNECTED     18470    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18469    
unix  3      [ ]         STREAM     CONNECTED     18456    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18455    
unix  3      [ ]         STREAM     CONNECTED     18384    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18383    
unix  3      [ ]         STREAM     CONNECTED     17886    @/var/run/hald/dbus-3gWpveZAD6
unix  3      [ ]         STREAM     CONNECTED     17885    
unix  3      [ ]         STREAM     CONNECTED     17884    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17883    
unix  2      [ ]         DGRAM                    17672    
unix  3      [ ]         STREAM     CONNECTED     17671    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     17670    
unix  3      [ ]         STREAM     CONNECTED     17665    @/var/run/hald/dbus-3gWpveZAD6
unix  3      [ ]         STREAM     CONNECTED     17664    
unix  3      [ ]         STREAM     CONNECTED     17602    @/var/run/hald/dbus-3gWpveZAD6
unix  3      [ ]         STREAM     CONNECTED     17564    
unix  3      [ ]         STREAM     CONNECTED     17343    @/var/run/hald/dbus-xFGKpTpvyx
unix  3      [ ]         STREAM     CONNECTED     17342    
unix  3      [ ]         STREAM     CONNECTED     17168    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17167    
unix  3      [ ]         STREAM     CONNECTED     17148    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17147    
unix  3      [ ]         STREAM     CONNECTED     16990    
unix  3      [ ]         STREAM     CONNECTED     16989    
unix  2      [ ]         DGRAM                    14786    
unix  3      [ ]         STREAM     CONNECTED     14741    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14740    
unix  3      [ ]         STREAM     CONNECTED     14735    
unix  3      [ ]         STREAM     CONNECTED     14734    
unix  2      [ ]         DGRAM                    14732    
unix  3      [ ]         STREAM     CONNECTED     14693    
unix  3      [ ]         STREAM     CONNECTED     14692

---

### Post by mistypotato on 2009-03-30
I wonder what all thouse Unix 3 streams are ?

---

### Post by scorp123 on 2009-03-31
> **mistypotato said:**
> I wonder what all thouse Unix 3 streams are ?
Wikipedia is your friend.

[http://en.wikipedia.org/wiki/Stream_(computing](http://en.wikipedia.org/wiki/Stream_(computing))

"... On Unix and related systems based on the C programming language, a stream is a source or sink of data, usually individual bytes or characters. Streams are an abstraction used when reading or writing files, or communicating over network sockets."

---

### Post by mistypotato on 2009-04-15
Still getting tons of NTP outbounds from one of my ubuntu servers and still haven't found anything that should be causing it.

Anyone ?

---

### Post by starz677 on 2012-03-14
> **scorp123 said:**
> That of course totally depends on what NTP package you installed. So why not check that instead?

```
sudo dpkg -l '*ntp*'
``` ... to this my server answers:
```
ii  ntp                                            1:4.2.4p0+dfsg-1ubuntu2.1                      Network Time Protocol daemon and utility programs
un  ntp-doc                                        <none>                                         (no description available)
un  ntp-refclock                                   <none>                                         (no description available)
un  ntp-server                                     <none>                                         (no description available)
un  ntp-simple                                     <none>                                         (no description available)
ii  ntpdate                                        1:4.2.4p0+dfsg-1ubuntu2.1                      client for setting system time from NTP servers
``` ... So I have two packages that are installed as can be seen by the "ii" marker.

Your result might be different. In any case it would be worth checking what config files are in those packages and where they are and what they are set to. To list the files inside a package you'd issue e.g. this command: ```
dpkg -L ntpdate
```To this my system responds with:
```
/.
/etc
/etc/dhcp3
/etc/dhcp3/dhclient-exit-hooks.d
/etc/dhcp3/dhclient-exit-hooks.d/ntpdate
/etc/default
**/etc/default/ntpdate**
/etc/logcheck
/etc/logcheck/ignore.d.server
/etc/logcheck/ignore.d.server/ntpdate
/etc/network
/etc/network/if-up.d
/etc/network/if-up.d/ntpdate
/usr
/usr/sbin
/usr/sbin/ntpdate-debian
/usr/sbin/ntpdate
/usr/share
/usr/share/doc
/usr/share/doc/ntpdate
/usr/share/doc/ntpdate/README.Debian
/usr/share/doc/ntpdate/copyright
/usr/share/doc/ntpdate/NEWS.Debian.gz
/usr/share/doc/ntpdate/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/ntpdate.8.gz
/usr/share/man/man8/ntpdate-debian.8.gz
```So the config file is here:
**/etc/default/ntpdate**

Again... your result might be different. But you should use some methodical way and analyse the causes for this behaviour step by step instead of jumping to any conclusions.

So depending on what the config file is you should take a look at it. Looking at my own file up there I can see these lines inside of it:
```
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# **Set to "yes" to take the server list from /etc/ntp.conf**, from package ntp,
# so you only have to keep it in one place.
**NTPDATE_USE_NTP_CONF=yes**

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="ntp.ubuntu.com"

# Additional options to pass to ntpdate
NTPOPTIONS=""
```See the line I highlighted? So if this setting is active then it does not matter what is configured here in this file ... the actual server list is taken from this file: **/etc/ntp.conf**

And when we look at that file we can see these lines in my case:
```
...
server ntp.ubuntu.com
server swisstime.ethz.ch
server bernina.ethz.ch
...
```So if I were not Swiss I might find it odd that my system tries to talk to some servers on a Swiss university (= ethz.ch is the "ETH Zurich").

What I'd suggest to you is that you please check ...
[LIST]
[*]which NTP packages are installed on your system?
[*]identify their config files
[*]check the configured settings
[*]compare the IP traffic you see with what is configured!
[/LIST]

If the destination servers are indeed NTP servers and they match the config files then I'd say your server was not compromised. If however your config files point to NTP servers in Europe and/or North America but your traffic is going to IP blocks assigned to some rather exotic places .. well, yes. That would be a different story.


Would your suggestions have been different if 

sudo dpkg -l '*ntp*'
Returned Zero ntp servers running ?
(And numerous ntp out-bounds were still being generated?)

---

### Post by oldos2er on 2012-03-14
Closed. Please start a new thread for your question; the one you posted in is three years old.

---

