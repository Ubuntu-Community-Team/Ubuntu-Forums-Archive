---
title: "proxychains dns resolution failure"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2016-10-28
Trying to get proxychains working on a 16.04 Desktop and can't get the dns lookup working.
My proxychains.conf looks like this

```
# proxychains.conf  VER 3.1
#
#        HTTP, SOCKS4, SOCKS5 tunneling proxifier with DNS.
#       

# The option below identifies how the ProxyList is treated.
# only one option should be uncommented at time,
# otherwise the last appearing option will be accepted
#
#dynamic_chain
#
# Dynamic - Each connection will be done via chained proxies
# all proxies chained in the order as they appear in the list
# at least one proxy must be online to play in chain
# (dead proxies are skipped)
# otherwise EINTR is returned to the app
#
strict_chain
#
# Strict - Each connection will be done via chained proxies
# all proxies chained in the order as they appear in the list
# all proxies must be online to play in chain
# otherwise EINTR is returned to the app
#
#random_chain
#
# Random - Each connection will be done via random proxy
# (or proxy chain, see  chain_len) from the list.
# this option is good to test your IDS :)

# Make sense only if random_chain
#chain_len = 2

# Quiet mode (no output from library)
#quiet_mode

# Proxy DNS requests - no leak for DNS data
proxy_dns

# Some timeouts in milliseconds
tcp_read_time_out 15000
tcp_connect_time_out 8000

# ProxyList format
#       type  host  port [user pass]
#       (values separated by 'tab' or 'blank')
#
#
#        Examples:
[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4  127.0.0.1 9050
socks5  127.0.0.1 9050

socks5  69.9.220.87     4554

```

My interface looks like this
```
nmcli device show enp9s0
GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         14:DA:E9:C8:C6:82
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     enp9s0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
IP6.ADDRESS[1]:                         fe80::16da:e9ff:fec8:c682/64
IP6.GATEWAY:                            

```

When I run proxychains I get the following
```
proxychains chromium-browser
ProxyChains-3.1 (http://proxychains.sf.net)
|DNS-request| apis.google.com 
|DNS-request| chrome.google.com 
|DNS-request| fonts.googleapis.com 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: apis.google.com does not exist
|DNS-response|: fonts.googleapis.com does not exist
|DNS-request| fonts.gstatic.com 
|DNS-request| lh3.googleusercontent.com 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: chrome.google.com does not exist
|DNS-request| lh4.googleusercontent.com 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: lh3.googleusercontent.com does not exist
|DNS-response|: fonts.gstatic.com does not exist
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-request| lh6.googleusercontent.com 
|DNS-response|: lh4.googleusercontent.com does not exist
|DNS-request| ssl.google-analytics.com 
|DNS-request| ssl.gstatic.com 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: lh6.googleusercontent.com does not exist

```

Why does DNS not find these servers?

---

### Post by lister171254 on 2016-11-04
DNS resolution works provided I don't use either Firefox or Chrome

```
llist@LeosLinux:~$ proxychains ping www.google.com
ProxyChains-3.1 (http://proxychains.sf.net)
ERROR: ld.so: object 'libproxychains.so.3' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
PING www.google.com (58.162.61.236) 56(84) bytes of data.
64 bytes from 58.162.61.236: icmp_seq=1 ttl=61 time=10.6 ms
64 bytes from 58.162.61.236: icmp_seq=2 ttl=61 time=10.0 ms
64 bytes from 58.162.61.236: icmp_seq=3 ttl=61 time=10.4 ms
64 bytes from 58.162.61.236: icmp_seq=4 ttl=61 time=10.2 ms
64 bytes from 58.162.61.236: icmp_seq=5 ttl=61 time=10.9 ms
64 bytes from 58.162.61.236: icmp_seq=6 ttl=61 time=20.9 ms
64 bytes from 58.162.61.236: icmp_seq=7 ttl=61 time=21.3 ms
^C
--- www.google.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6007ms
rtt min/avg/max/mdev = 10.094/13.536/21.339/4.832 ms

```

But in both Firefox and Chrome I get DNS errors

```
llist@LeosLinux:~$  proxychains chromium-browser
ProxyChains-3.1 (http://proxychains.sf.net)
[12982:12982:1104/174927:ERROR:gl_surface_glx.cc(91)] glXGetFBConfigs failed.
[12982:12982:1104/174927:ERROR:gl_surface_glx.cc(91)] glXGetFBConfigs failed.
[12982:12982:1104/174927:ERROR:gl_context_glx.cc(68)] Failed to create GL context with glXCreateNewContext.
[12982:12982:1104/174927:ERROR:gpu_info_collector.cc(46)] gl::init::CreateGLContext failed
[12982:12982:1104/174927:ERROR:gpu_info_collector.cc(114)] Could not create context for info collection.
[12982:12982:1104/174927:ERROR:gpu_main.cc(503)] gpu::CollectGraphicsInfo failed (fatal).
[12982:12982:1104/174928:ERROR:gpu_child_thread.cc(390)] Exiting GPU process due to errors during initialization
|DNS-request| fast.fonts.net 
|DNS-request| cdn.siftscience.com 
|DNS-request| www.google-analytics.com 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: fast.fonts.net does not exist
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: cdn.siftscience.com does not exist
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: www.google-analytics.com does not exist
|DNS-request| hexagon-analytics.com 
|DNS-request| syd.m-cdn.com 
|DNS-request| ssl.google-analytics.com 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-response|: hexagon-analytics.com does not exist
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied
|DNS-request| v2.zopim.com 
|DNS-response|: syd.m-cdn.com does not exist
|DNS-response|: ssl.google-analytics.com does not exist
|DNS-request| www.mammoth.com.au 
|S-chain|-<>-127.0.0.1:9050-<>-127.0.0.1:9050-<--denied

```

---

### Post by lister171254 on 2016-11-04
Hmmm,
Just changed from strict_chain to dynamic_chain in proxychains.conf and everything works now.

---

