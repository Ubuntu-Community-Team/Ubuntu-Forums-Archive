---
title: "Cannot access certain sites... all Google servers, etc. -- Not DNS Issue!"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by The_PHP_Jedi on 2007-11-16
Since a couple of days ago, I have not been able to access any Google server (google.com, GMail, Orkut, etc...). I have done testing, and this only occurs on my Ubuntu install, not Windows on this box nor any other device (laptop w/ Win XP, PDA, etc.).

I have checked network configuration... no changes... I have tested DNS servers, ping, etc... DNS is fine (I get the DNS records for _all_ websites) but cannot ping or traceroute Google servers and a few other websites. This is system wide, not browser specific. I used to use my local BIND server, but since the problem arose, it has not been responding, which is when I switched to my ISP's DNS (and yes, I've tried w/ OpenDNS, but DNS is not the issue here).

I have messed around with the network config, even re-making the config file manually, to no avail.
It is a very odd issue.. and I was planning to switch to Debian soon, as I'm very experienced with Linux, and only kept Ubuntu for my parents, but Ubuntu does save some time with it's GUI tools and general ease of use, which is going to take some time to set up manually on Debian.

Throw me the most complex stuff you got, I'm an experienced user.

Summary:
-DNS is _not_ the issue (I know that's what you guys will point at first)
-Cannot ping/traceroute Google servers and a few other websites
-Only occurs in Ubuntu

Any help is appreciated! Many thanks to the Linux community!

---

### Post by intelligentfool on 2007-11-16
so you can ping DNS servers, are the google domains resolving or are you not even getting that much? 
If they're not resolving, maybe its a cached ARP issue on your router/switch?
If they are resolving, what does a ping and tracert show for those IPs? (i cant ping the google.com IP's from work, but im not sure if thats our network or the carriers that's dropping ICMP)

its basic, i know, but you gota start simple :)

---

### Post by The_PHP_Jedi on 2007-11-16
Maybe I wasn't clear enough.. I can't ping Google servers, and a few other websites... but I can ping and get a DNS response with no problem.. I get Google's IP from my DNS, but can't ping the Google servers.

These are the Google servers I get...
72.14.207.99 64.233.187.99 64.233.167.99

Thanks for helping :)

thephpjedi@thephpjedi-desktop:~$ traceroute google.com
traceroute to google.com (72.14.207.99), 30 hops max, 40 byte packets
 1  * * *
and it goes on with the same output...
Also I've reset the modem many times... it even went back to default settings because of a power failure.

---

### Post by intelligentfool on 2007-11-16
can you script out a HTTP GET from those IP's? I think google turns off ICMP to help prevent DDOS attacks, etc, but a CLI HTTP GET should at least return some kind of HTTP error code, right? unless the site is truly unreachable, then something else is up. 

your thinking its in your ubuntu config somewhere though, right?

---

### Post by The_PHP_Jedi on 2007-11-16
well, now I'm having issues even starting apache... doesn't seem to be able to connect... but the server's started.. that's just a side note.

Yeah, the issues is definitely my ubuntu install, since it works in other OSes perfectly, and in other devices. (Win XP:This desktop, laptop, WM5:PDA)

atm this is what I get from wget:
thephpjedi@thephpjedi-desktop:~$ wget google.com
--20:18:27--  [http://google.com/](http://google.com/)
           => `index.html.1'
Resolving google.com... 72.14.207.99, 64.233.187.99, 64.233.167.99
Connecting to google.com|72.14.207.99|:80... failed: Connection timed out.
Connecting to google.com|64.233.187.99|:80...

---

### Post by intelligentfool on 2007-11-16
hmm, i cant think of what would be the cause right now. i'm still learning linux myself, although i'm somewhat more knowledgeable in networking. i'll post if i think of something. good luck.

---

### Post by The_PHP_Jedi on 2007-11-16
well ubuntu officially ate its own ***... it hangs at "Starting NFS common utilities" during boot sequence...
I'll install Debian as planned and use that instead of Ubuntu...

Thanks for the help anyways... if anyone still has a solution, please post.. I'll be watching this, and keeping my broken Ubuntu install partition.

---

### Post by conjur3r on 2007-11-16
The problem lies in your network routing.  You probably do not have a default route inserted.  Next time you're in ubuntu, do this:

# netstat -rn

and search for a line starting with 0.0.0.0 as this defines your default route.  This is the path it takes when the OS doesn't know where to send the packets to.  Try adding a default route with the following substituting GATEWAY_IP with the ip address of your gateway/router:

# sudo route add default gw GATEWAY_IP

---

### Post by The_PHP_Jedi on 2007-11-17
That didn't work conjur3r... instead I was given this error message: SIOCADDRT: No such device

Any help is still appreciated.. I'm really getting lazy and don't want to set up a new Debian install... just want to keep this Ubuntu install.

---

### Post by GladRagKraken on 2007-11-17
I've got an incredibly similar problem, from being able to resolve google server's ips, but not being able to ping them, and receiving an error message while 'wget'ing them.  I don't have this problem for [www.google.com](www.google.com), but I do receive this problem for mail.google.com, as well as a few other sites. (Achewood? what will I do w/o my comics? 'google.com' w/o the www prefix, others)  This problem first started after trying to set up python-django-postgresql-psycopg2-pgadmin3 for goofing around with, if I could have broken something trying to get all that to work.


To reiterate:

Pinging and wgeting mail.google.com:

~$ping mail.google.com
PING googlemail.l.google.com (74.125.19.19) 56(84)
^c                    (break cause I forgot to tell it when to stop)
--- googlemail.l.google.com ping statistics ---
234 packets transmitted, 0 received, 100% packet loss, time 233025ms

~$wget mail.google.com
--21:46:34--  [http://mail.google.com/](http://mail.google.com/)
                  => 'index.html'
Resolving mail.google.com... 74.125.19.18, 74.125.19.17, 74.125.19.83, ...
Connecting to mail.google.com|74.125.19.18|:80... failed: Connection timed out.
Connecting to mail.google.com|74.125.19.17|:80... failed: Connection timed out.
Connecting to mail.google.com|74.125.19.83|:80... failed: Connection timed out.
Connecting to mail.google.com|74.125.19.19|:80... failed: Connection timed out.
Retrying.
(at which point I got bored)

I'm not convinced it's not a dns issue.  When I bring the laptop into the office, gmail loads, (still no achewood though) which suggests that the dns I'm picking up from the router there is less messed up by my configuration than the one at home.

It's interesting to note that the router at home uses openDNS, which works just fine on the windows machines.  I went to openDNS's site and had them refresh mail.google.com, but that didn't seem to do anything.

Anyhow, on to the stuff that wasn't included in php_jedi's description.  Or rather, the things I've tried that he hadn't. All without noticeable change.  Moral of the story; he knew not to bother trying?

Disabling IpV6 in firefox and /etc/modprobe.d/aliases

Changing /ets/hosts from

127.0.0.1 localhost
127.0.1.1 ubuntu.sys76.lan ubuntu  

to

127.0.0.1 localhost ubuntu.sys76.lan ubuntu


Anyhow, I'm not really sure what the problem is, and I'm at my ropes end trying to figure out different things it could be.  Anybody got any ideas what it could be?

---

### Post by GladRagKraken on 2007-11-17
W/r/t # sudo route add default GATEWAY_ADDRESS

I get an error,

SIOCADDRT: No such device

despite my first 0.0.0.0 line reading
0.0.0.0     GATEWAY_ADDRESS     0.0.0.0     UG     0 0    eth1 

Where gateway address is checked with other computers and the ubuntu box as leading to my router.

---

### Post by conjur3r on 2007-11-17
Sorry, I had a mistake in the route command, it should be the following:

# sudo route add default gw GATEWAY_IP

Make sure you substitute GATEWAY_IP with the real ip address of your router/gateway.

---

### Post by intelligentfool on 2007-11-17
if the router is running DHCP shouldnt it be passing the default gateway down to clients along with their IP's and subnet masks? default gateway doesnt seem to be a likely cause, otherwise wouldnt the vast majority of IP's be unreachable?

---

### Post by GladRagKraken on 2007-11-17
Well, it turns out that the router is passing the gateway on.  Attempting to add the router as a default gateway as suggested above returns a 

SIOCADDRT: File exists

error.  Any other thoughts as to the cause of this problem?

---

### Post by intelligentfool on 2007-11-17
this might be kinda dumb, but have either of you tried the live cd to see if the problem still exists? php_jedi said his dual boot machine doesnt show the problem when in windows, but without knowing more about how linux works, i find it hard to believe that a bad config somewhere would cause particular IP's to be unreachable, leaving the vast majority untouched and still reachable. 

i'd really love to know the cause of this. 

try the live cd's, let us know what happens.

---

### Post by conjur3r on 2007-11-17
Yes, I agree that a dhcp setup should provide clients with everything it needs to be networkable but sometimes anonamlies can occur in between renewals.

Are you able to provide the output of the following?

# netstat -rn

# sudo iptables -L

---

### Post by The_PHP_Jedi on 2007-11-17
> **intelligentfool said:**
> this might be kinda dumb, but have either of you tried the live cd to see if the problem still exists? php_jedi said his dual boot machine doesnt show the problem when in windows, but without knowing more about how linux works, i find it hard to believe that a bad config somewhere would cause particular IP's to be unreachable, leaving the vast majority untouched and still reachable. 

i'd really love to know the cause of this. 

try the live cd's, let us know what happens.

Live CD works fine. Installed Debian, no problems 'till now... but I'm still wanting to get Ubuntu working...

I think I have identified the problem. During bootup, when 'Starting NFS common utilities', it tries to connect locally to either the dbus server or something else locally... that's not responding (for whatever reason), and it hangs for about 5 minutes or so, until it times out. I have been experiencing the same symptoms when pinging localhost (127.0.0.1). I cannot start my MySQL server, and apache doesn't respond locally.

In short, network drivers/config is messed up, and not allowing/starting/listening/whatever connections locally... (maybe the device got misconfigured somehow or something?)

thephpjedi@thephpjedi-desktop:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [fail] 

> **conjur3r said:**
> Yes, I agree that a dhcp setup should provide clients with everything it needs to be networkable but sometimes anonamlies can occur in between renewals.

Are you able to provide the output of the following?

# netstat -rn

# sudo iptables -L

Here's the output...

thephpjedi@thephpjedi-desktop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 eth0

thephpjedi@thephpjedi-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
moblock_in  0    --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
moblock_fw  0    --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
moblock_out  0    --  anywhere             anywhere            state NEW 

Chain moblock_fw (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

---

### Post by The_PHP_Jedi on 2007-11-17
***SOLVED***

I had forgotten I had installed moblock (pkg: moblock-nfq) (peerguardian for linux)... I removed it and its all fixed... I need to keep a list of things I install... I had removed the other two apps I had installed, but I forgot of moblock, hehe....

Thanks again! Sorry for the trouble.

---

### Post by conjur3r on 2007-11-17
Glad you solved it.  Always the firewall!

---

### Post by GladRagKraken on 2007-11-17
Oh sonofa .  . . Yeah.  removing moblock removes the problem.  Thanks so much, everyone.

---

### Post by The_PHP_Jedi on 2007-11-17
hehe, no problem... always gotta have the forums to save ya!

---

### Post by infurnus on 2007-11-19
Heh i spent about 3 hrs on this and finally found this thread i had the same problem with the same solution BTW in the mean time i was able to use TOR to get to google.

---

### Post by whatrucrazy on 2007-11-28
that was it for me too!
hours of pain, punching commands in and cursing... when all I had to do was read to the end of the thread.


thanks all!

---

