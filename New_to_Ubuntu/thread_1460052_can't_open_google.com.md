---
title: "can't open google.com"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by xumuk37 on 2010-04-22
Hi Folks, i was trying up chrome extenstions when suddenly i couldn't access some sites not only google but any search engine... ping google.com returns... 

# ping google.com
PING google.com (209.85.229.99) 56(84) bytes of data.
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_seq=1 ttl=46 time=55.8 ms
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_seq=2 ttl=46 time=57.7 ms
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_seq=3 ttl=46 time=56.3 ms
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_seq=4 ttl=46 time=57.0 ms
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_seq=5 ttl=46 time=57.4 ms
^C
--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 55.827/56.901/57.723/0.701 ms

but when i try to open it in any browser it doesn't...

---

### Post by Grenage on 2010-04-22
Does the browser have any DNS settings in it?  What I mean is, can it be configured to use DNS settings other than those used by the main system?

That would be my first thing to check, other than removing whatever extensions I had installed.

---

### Post by xumuk37 on 2010-04-22
I've already purged chrome with all extensions... I tried with opera and firefox and no, they don't have any own DNS settings...

---

### Post by sunk8 on 2010-04-22
> **xumuk37 said:**
> Hi Folks, i was trying up chrome extenstions when suddenly i couldn't access some sites not only google but any search engine... ping google.com returns... 
--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 55.827/56.901/57.723/0.701 ms

but when i try to open it in any browser it doesn't...

Well, your DNS seems fine... It's a browser issue...
Firefox will work fine...

Go to Settings >> Extensions disable them and try to isolate the one causing the issue...
Do let the chrome people know abt this problem so they can improve their browser further...

---

### Post by sunk8 on 2010-04-22
> **xumuk37 said:**
> I've already purged chrome with all extensions... I tried with opera and firefox and no, they don't have any own DNS settings...

Your DNS addresses are usually saved at /etc/resolv.conf
Did you change them by any chance?
I use OpenDNS servers...

---

### Post by xumuk37 on 2010-04-22
[SOLVED] adding 
prepend domain-name-servers 208.67.220.220 208.67.222.222;
to /etc/dhcp3/dhclient.conf

Thanks for help :)

---

