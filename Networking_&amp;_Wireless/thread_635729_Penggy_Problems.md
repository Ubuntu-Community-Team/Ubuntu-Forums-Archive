---
title: "Penggy Problems"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by evilseth on 2007-12-09
Hello all. 

I know no one recommends AOL, but I'm stuck with it.
I managed to get Penggy installed and dialing, but once a connection is made it executes the chat script and then shows a 'segmenation fault'. I am unable to get an Internet connection. 

> Parsing config file: /etc/penggy/penggy.cfg

Checking options:
  access_method = modem
  protocol = p3
  interface_type = tun
  secret_file = /etc/penggy/aol-secrets
  screen_name = (hidden)
  auto_reconnect = true
  reconnect_delay = 5
  daemon = false
  debug_level = 5
  set_dns = true
  pid_file = /var/run/penggy.pid
  modem_device = /dev/modem
  lock_path = /var/lock
  rtscts = true
  initstr1 = AT&FL1
  dialstr = ATDT
  phonetab = /etc/penggy/phonetab
  line_speed = 115200
  dial_retry = 1
  retry_delay = 2

Using /dev/modem device...
Device /dev/modem opened
Dialing provider...
Sending: AT&FL1
Received line : OK
Dialing 2262108
Sending: ATDT2262108
Received line : CONNECT 115200 
[B]Connection at 115200b/s done.
Executing chat script (/usr/share/penggy/chat/aolnet.scm)...
Segmentation fault (core dumped)[/B]


Any ideas? Any help would be greatly appreciated.

---

### Post by evilseth on 2007-12-21
bump

---

