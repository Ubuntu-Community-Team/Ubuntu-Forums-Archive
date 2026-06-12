---
title: "can i use cli web browser to config router ??"
date: 2022-08-05
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-08-05
i want to config router admin page
which one should i use ??

---

### Post by mIk3_08 on 2022-08-05
> **chat-4432 said:**
> i want to config router admin page
which one should i use ??
Usually to configure a router they will use a web browser. I don't know what router you have. Just check your router guide so you will know how you can configure it. By the way, what router you have? Regards and cheers.

---

### Post by mIk3_08 on 2022-08-05
> **chat-4432 said:**
> "can i use cli web browser to config router ?? " Yes, you can. there are a lot of cli web browser. Just search around. Regards and cheers.

---

### Post by TheFu on 2022-08-05
It depends on the router web-app and if it uses features not supported by the browser you want to use or not. Most consumer routers are php+javascript webapps and I don't know of any CLI-based browser that supports javascript at all.  It is the main feature I look for in browsers - NOT supporting javascript.

Some enterprise routers allow configuration without any GUI.  They typically have a shell login or serial connection supported.  My router supports both. 99% of the time I ssh into the CLI interface and perform normal maintenance, log review, and updates that way, but some features like viewing bandwidth and traffic graphs requires the javascript-based webapp.

Here's the ssh/serial console interface:
```
  0) Logout                              7) Ping host
  1) Assign interfaces                   8) Shell
  2) Set interface IP address            9) pfTop
  3) Reset the root password            10) Firewall log
  4) Reset to factory defaults          11) Reload all services
  5) Power off system                   12) Update from console
  6) Reboot system                      13) Restore a backup
```
I didn't include the summary at the top which shows how each interface is configured for different subnets, nor the public ssh keys.  I usually patch on Friday nights, but I think everyone is gone for the weekend already - patching now.
....
```
Starting web GUI...done.
Generating RRD graphs...done.
```

that was easy. No reboot needed, but did get 2 updated packages.  The update replace the current webapp for a new version and it re-created the fancy RDD graphs.

---

### Post by chat-4432 on 2022-08-07
i try to use links2
when i try links2 -g [http://localhost:9090](http://localhost:9090)
it show 
```
error
error loading [http://localhost:9090/:](http://localhost:9090/:)
Connectin refused
``` 
what should i do ??

---

