---
title: "proxy checker"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by stonecoldjha on 2011-04-06
Hey there.....
i had been a user of ubuntu for almost 1.5 years, before i switched back to windows again for a simple reason that for the past few months, our campus network connection has been behaving really erratically. what i mean is....we have a number of proxy servers that we make use of...which are behaving in such a manner...at times a proxy is real fast...and moments later it starts to crawl...so i have to constantly see as to which proxies are running fastest. in windows, there is a small piece of software called quick tools in which there is a tool called proxy checker...that i use to rank proxies in the order of how fast they are at a given point of time....then i click "make IE proxy" after choosing the fastest one...and that proxy works for chrome and firefox both...i have to do this many times while browsing to get good speeds... 
is there a similar easy to use tool for ubuntu that can make such changes?????

---

### Post by HermanAB on 2011-04-06
Foxyproxy, Proxy tool, Toggle proxy, Go2 proxy, Proxy selector, Elite proxy switcher, Environment proxy, Proxy switcher...?

---

### Post by stonecoldjha on 2011-04-06
is anyone of them capable of listing proxies on the basis of speed?

---

### Post by karvol on 2011-04-16
same problem here !!

---

### Post by GWBouge on 2011-04-16
I just threw together this little Python script that might work for you.  All it does is check the ping times to a list of proxies (not actual transfer speeds), picks the fastest, and updates your system-wide proxy settings to use it.  Note:  I just used a few proxies from [http://publicproxyservers.com/]("http://publicproxyservers.com/") to test it out with, so replace those with the names/IP's of whatever you want to work with.

```
#! /usr/bin/python

import sys
import gconf
from subprocess import Popen, PIPE

proxy_list = [
	'1tunnels.info',
	'chemistsproxy.info',
	'quicksurfing.info'
]

times = []

for proxy in proxy_list:
	try: times.append(int(Popen('ping %s -c 4 | grep \'packets transmitted\' | awk -F time \'{print $2}\' | awk -F ms \'{print $1}\'' % proxy, shell=True, stdout=PIPE).stdout.read().lstrip().rstrip()))
	except: proxy_list.remove(proxy)

if len(times) == 0:
	print("Could not resolve proxies, exiting ...")
	sys.exit(2)

i = times.index(min(times))
proxy = proxy_list[i]

g = gconf.client_get_default()
g.set_string('/system/proxy/mode', 'manual')
g.set_string('/system/http_proxy/host', proxy)
g.set_bool('/system/http_proxy/use_http_proxy', True)

```

---

