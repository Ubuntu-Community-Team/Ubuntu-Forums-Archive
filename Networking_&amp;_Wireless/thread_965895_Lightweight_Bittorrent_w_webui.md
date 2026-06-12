---
title: "Lightweight Bittorrent w/ webui"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Bllz on 2008-10-31
Hi, I'm building a dedicated BT download server and I need a client with several specific features.

The client has to be relatively lightweight, capable of proxifying tracker connections through a SOCKS5 proxy, and it must have a stable and intuitive webUI.

I've tried rtorrent, but then discovered that it had no proxy support.  I also tried deluge, but the webUI had all sorts of strange bugs.

Transmission also wouldn't forward ports properly, though I don't know why.

Any suggestions?

---

### Post by vitorgatti on 2008-10-31
My Deluge's WebUI is perfectly normal.
In its config, try to change "advanced" to "deluge", and see if it gets better.

:KS

---

### Post by Bllz on 2008-11-02
> **vitorgatti said:**
> My Deluge's WebUI is perfectly normal.
In its config, try to change "advanced" to "deluge", and see if it gets better.

:KS

I'll certainly try that.  I did like Deluge while it worked =)

What's the path to the config file?

---

### Post by Bllz on 2008-11-02
Here's the output of the error I'm getting in the webUI of Deluge:

```
--Deluge Error--
KeyError : 'all'
path : /index
file : /usr/share/deluge/plugins/WebUi/webserver_framework.py in filter_torrent_state, line 292

--Input--
<Storage {'filter': 'all'}>

--Versions--
WebUi : rev.172
Python : 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2]
dbus:0.82.4

--Traceback--
  File "/usr/share/deluge/plugins/WebUi/lib/webpy022/webapi.py", line 304, in wsgifunc
    result = func()
  File "/usr/share/deluge/plugins/WebUi/lib/webpy022/request.py", line 131, in <lambda>
    func = lambda: handle(inp, fvars)
  File "/usr/share/deluge/plugins/WebUi/lib/webpy022/request.py", line 61, in handle
    return tocall(*([x and urllib.unquote(x) for x in args] + fna))
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 151, in deco
    return func(self, name) #ok, continue..
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 135, in deco
    res = func(self, name)
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 168, in deco
    return func(self, name)
  File "/usr/share/deluge/plugins/WebUi/deluge_webserver.py", line 107, in GET
    torrent_list = filter_torrent_state(torrent_list, vars.filter)
  File "/usr/share/deluge/plugins/WebUi/webserver_framework.py", line 293, in filter_torrent_state
    filter_func = filters[filter_name]




```

---

