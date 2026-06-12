---
title: "trying to get DNS caching working right"
date: 2019-09-18
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2019-09-18
at this point i am unable to get the "unbound" DNS caching server to run.  it ran when it was first installed but after a reboot it would never start up.  it is complaining about an invalid key for the control port.

i hear that systemd has a resolver, but it seems to be missing on my system while the rest of systemd is running.  systemd is just all too confusing.

all this came about because 2 programs were ignoring the [COLOR=#0000cd]**[FONT=courier new]/etc/resolv.conf[/FONT]**[/COLOR] file (which directed queries to 3 particular IP addresses offsite) and sending queries to 127.0.0.1.  so the idea has been to get a DNS cache running that would listen on 127.0.0.1 (only) and forward all queries to any of the IP addresses i configure it to forward to.  local caching is fine, but i do *not* want it to directly do recursive resolving.  it must send all DNS queries to one of those addresses.

i was just reading about dnsmasq.  i does DHCP and TFTP, too.  but i could not find how to turn those off.  i do not want either of those to be run, just DNS caching and forwarding only.

a program that does *just* DNS forwarding and (optionally) caching, *only*, would be great.  high performance is not needed.

is there anyone around that knows about today's DNS software? or do i need to accept local resolving and run BIND? also, does anyone know why [COLOR=#0000cd]**ntpd**[/COLOR] ignores [COLOR=#0000cd]**[FONT=courier new]/etc/resolv.conf[/FONT]**[/COLOR]?

---

### Post by pcfan1234 on 2019-09-18
Systemd-resolve listens on 127.0.0.53 not on 127.0.0.1. You need 18.04 or newer to use that by default, older versions use dnsmasq-base listening on 127.0.0.1.
DO NOT EDIT /etc/resolv.conf. On 18.04 it must only contain 
> 
nameserver 127.0.0.53
and nothing else.

---

### Post by SeijiSensei on 2019-09-18
> i hear that systemd has a resolver, but it seems to be missing on my system while the rest of systemd is running. systemd is just all too confusing.

The last time we chatted about this you had removed systemd-resolved.  Did you reinstall it?

---

### Post by Skaperen on 2019-09-18
it's not listening to anything on my 18.04 Xubuntu system.  and, ntp really is sending queries to 127.0.0.1 port 53:

```

lt2a/root /root 14# tcpdump -llni any port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 262144 bytes
15:26:28.799138 IP 127.0.0.1.55208 > 127.0.0.1.53: 28334+ A? 1.ubuntu.pool.ntp.org. (39)
15:26:28.799169 IP 127.0.0.1.55208 > 127.0.0.1.53: 52156+ AAAA? 1.ubuntu.pool.ntp.org. (39)
15:26:28.799203 IP 127.0.0.1.36790 > 127.0.0.1.53: 28334+ A? 1.ubuntu.pool.ntp.org. (39)
15:26:28.799217 IP 127.0.0.1.36790 > 127.0.0.1.53: 52156+ AAAA? 1.ubuntu.pool.ntp.org. (39)
15:26:29.799167 IP 127.0.0.1.41105 > 127.0.0.1.53: 56896+ A? ntp.ubuntu.com. (32)
15:26:29.799207 IP 127.0.0.1.41105 > 127.0.0.1.53: 54606+ AAAA? ntp.ubuntu.com. (32)
15:26:29.799252 IP 127.0.0.1.36093 > 127.0.0.1.53: 56896+ A? ntp.ubuntu.com. (32)
15:26:29.799267 IP 127.0.0.1.36093 > 127.0.0.1.53: 54606+ AAAA? ntp.ubuntu.com. (32)
15:26:34.799318 IP 127.0.0.1.38082 > 127.0.0.1.53: 16466+ A? 0.ubuntu.pool.ntp.org. (39)
15:26:34.799378 IP 127.0.0.1.38082 > 127.0.0.1.53: 43368+ AAAA? 0.ubuntu.pool.ntp.org. (39)
15:26:34.799451 IP 127.0.0.1.37174 > 127.0.0.1.53: 16466+ A? 0.ubuntu.pool.ntp.org. (39)
15:26:34.799476 IP 127.0.0.1.37174 > 127.0.0.1.53: 43368+ AAAA? 0.ubuntu.pool.ntp.org. (39)
15:27:09.799320 IP 127.0.0.1.38959 > 127.0.0.1.53: 34418+ A? 2.ubuntu.pool.ntp.org. (39)
15:27:09.799376 IP 127.0.0.1.38959 > 127.0.0.1.53: 24713+ AAAA? 2.ubuntu.pool.ntp.org. (39)
15:27:09.799451 IP 127.0.0.1.38646 > 127.0.0.1.53: 34418+ A? 2.ubuntu.pool.ntp.org. (39)
15:27:09.799478 IP 127.0.0.1.38646 > 127.0.0.1.53: 24713+ AAAA? 2.ubuntu.pool.ntp.org. (39)
15:27:12.799312 IP 127.0.0.1.45265 > 127.0.0.1.53: 44106+ A? 3.ubuntu.pool.ntp.org. (39)
15:27:12.799370 IP 127.0.0.1.45265 > 127.0.0.1.53: 44131+ AAAA? 3.ubuntu.pool.ntp.org. (39)
15:27:12.799443 IP 127.0.0.1.45486 > 127.0.0.1.53: 44106+ A? 3.ubuntu.pool.ntp.org. (39)
15:27:12.799469 IP 127.0.0.1.45486 > 127.0.0.1.53: 44131+ AAAA? 3.ubuntu.pool.ntp.org. (39)
15:27:31.492751 IP 192.0.2.2.51455 > 209.244.0.4.53: 16348+ [1au] A? safebrowsing.googleapis.com. (56)
15:27:31.492784 IP 192.0.2.2.51455 > 209.244.0.4.53: 3835+ [1au] AAAA? safebrowsing.googleapis.com. (56)
15:27:31.494178 IP 192.0.2.2.33689 > 209.244.0.4.53: 27088+ [1au] A? safebrowsing.googleapis.com. (56)
15:27:31.673674 IP 209.244.0.4.53 > 192.0.2.2.51455: 16348 1/0/1 A 216.58.207.138 (72)
15:27:31.674117 IP 209.244.0.4.53 > 192.0.2.2.51455: 3835 1/0/1 AAAA 2a00:1450:4016:807::200a (84)
15:27:31.674178 IP 209.244.0.4.53 > 192.0.2.2.33689: 27088 1/0/1 A 172.217.169.106 (72)
15:27:32.798907 IP 127.0.0.1.59687 > 127.0.0.1.53: 56378+ A? 1.ubuntu.pool.ntp.org. (39)
15:27:32.798930 IP 127.0.0.1.59687 > 127.0.0.1.53: 15427+ AAAA? 1.ubuntu.pool.ntp.org. (39)
15:27:32.798951 IP 127.0.0.1.49285 > 127.0.0.1.53: 56378+ A? 1.ubuntu.pool.ntp.org. (39)
15:27:32.798971 IP 127.0.0.1.49285 > 127.0.0.1.53: 15427+ AAAA? 1.ubuntu.pool.ntp.org. (39)
15:27:34.799217 IP 127.0.0.1.38088 > 127.0.0.1.53: 15394+ A? ntp.ubuntu.com. (32)
15:27:34.799281 IP 127.0.0.1.38088 > 127.0.0.1.53: 64822+ AAAA? ntp.ubuntu.com. (32)
15:27:34.799361 IP 127.0.0.1.43923 > 127.0.0.1.53: 15394+ A? ntp.ubuntu.com. (32)
15:27:34.799396 IP 127.0.0.1.43923 > 127.0.0.1.53: 64822+ AAAA? ntp.ubuntu.com. (32)
15:27:41.799308 IP 127.0.0.1.41327 > 127.0.0.1.53: 23126+ A? 0.ubuntu.pool.ntp.org. (39)
15:27:41.799370 IP 127.0.0.1.41327 > 127.0.0.1.53: 8556+ AAAA? 0.ubuntu.pool.ntp.org. (39)
15:27:41.799445 IP 127.0.0.1.46118 > 127.0.0.1.53: 23126+ A? 0.ubuntu.pool.ntp.org. (39)
15:27:41.799476 IP 127.0.0.1.46118 > 127.0.0.1.53: 8556+ AAAA? 0.ubuntu.pool.ntp.org. (39)
^C
38 packets captured
70 packets received by filter
0 packets dropped by kernel
lt2a/root /root 15# cat /etc/resolv.conf
nameserver 209.244.0.4
nameserver 208.67.222.220
nameserver 1.0.0.1
options edns0
lt2a/root /root 16# netstat -antup|fgrep 53
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           858/avahi-daemon: r 
udp6       0      0 :::5353                 :::*                                858/avahi-daemon: r 
lt2a/root /root 17# 


```
so is the real problem in ntp?  a while back i did install a different ntp server, the one from openbsd, and it did the same thing.

---

### Post by SeijiSensei on 2019-09-18
If you're using systemd-resolved, /etc/resolv.conf should have only one nameserver entry for 127.0.0.53.

---

### Post by Skaperen on 2019-09-18
> The last time we chatted about this you had removed systemd-resolved.  Did you reinstall it?

something asked if it could be disabled, default yes, so i pressed return.  i use offsite resolvers so it was not a worry then. it may have uninstalled it.

also, what good would it be to put 127.0.0.53 in /etc/resolv.conf since ntpd doesn't use it.  other programs do use it and i don't want to change where their queries go to.  i do not want to use a local recursive resolver for other programs.  but, doing so for ntpd is ok.

---

### Post by Skaperen on 2019-09-18
> **pcfan1234 said:**
> Systemd-resolve listens on 127.0.0.53 not on 127.0.0.1. You need 18.04 or newer to use that by default, older versions use dnsmasq-base listening on 127.0.0.1.
DO NOT EDIT /etc/resolv.conf. On 18.04 it must only contain 

and nothing else.

it does not contain that.  it containers the IPs of the servers i intend to use.  it was put in place the day i installed xubuntu 18.04.  ntpd should be using it.  everything else does.

---

### Post by Skaperen on 2019-09-18
i ran a test program and confirmed this: for both TCP and UDP, anything listening on 127.0.0.1 gets traffic addressed to any IP in 127.0.0.0/8.  well, i didn't actually test 127.0.0.0 or 127.255.255.255.  and i didn't test all 16777214 other IPs (just 3 of them).  so, a server listening on 127.0.0.1 would get traffic addressed to 127.0.0.53 and visa-versa.

---

### Post by Skaperen on 2019-09-18
i reinstalled unbound.  it's running.
i stopped it and started it.  it's running.
i stopped it.  it's down.
i copied the example config file from the man page, unmodified, and started it.  i got the same error as i was getting before.
i moved the example config file to /root to hang on to it and started unbound.  it's running..

i could just leave it that way, but i want it to forward all queries to one of the preferred servers.  right now it's doing resolving (and presumably caching).

has anyone reading this modified or replaced the config file and gotten it to run?

i saw some postings that suggested [COLOR=#0000cd][FONT=courier new]**ntpd**[/FONT][/COLOR] has some kind of [COLOR=#0000cd][FONT=courier new]**apparmor**[/FONT][/COLOR] issue.  has anyone heard about that?

---

### Post by Skaperen on 2019-09-19
i figured out why [COLOR=#0000cd][FONT=courier new]**ntpd**[/FONT][/COLOR] was ignoring [COLOR=#0000cd][FONT=courier new]**/etc/resolv.conf**[/FONT][/COLOR].  it couldn't read it because i had [COLOR=#0000cd][FONT=courier new]**/etc/resolv.conf**[/FONT][/COLOR] symlinked to a different file (so i could easily switch it around to rotate the 3 IPs in it).  [COLOR=#0000cd][FONT=courier new]**apparmor**[/FONT][/COLOR] is restricting [COLOR=#0000cd][FONT=courier new]**ntp**[/FONT][/COLOR] to only read specific files.  it includes [COLOR=#0000cd][FONT=courier new]**/etc/resolv.conf**[/FONT][/COLOR] but not what it points to.  so i changed it to just copy the file (to a temporary new file then move that into place) instead of making a symlink.  now [COLOR=#0000cd][FONT=courier new]**ntpd**[/FONT][/COLOR] queries the correct name servers.

---

