---
title: "Running a Proxy Server, Questions"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by jbaerboc on 2015-08-17
So I have the goal of running my own proxy server off my home computer. Can be a Linux OS or Windows OS, whichever gets me where I need to go.

1. Need a solution that does not require tinkering with the home LAN router [controlled by ISP so I have no access].
2. Needs to be something I can connect to from outside my home network [is it possible with my #1 requirement?].
3. GUI setup/control preferred.

Anyone have any ideas? Again I can host this in Linux or my newly upgraded Windows 10, whichever has the program comparability for whatever will work.

Thanks!

---

### Post by TheFu on 2015-08-17
**squid** is the normal outbound proxy server used on Linux. 
[https://help.ubuntu.com/14.04/serverguide/squid.html](https://help.ubuntu.com/14.04/serverguide/squid.html)

1 - If you can't make squid the default gateway, then every client device will need to be manually changed to point to the proxy system.
2 - if you cannot control port forwarding on the edge router, then you cannot have remote access.
3 - there may be a GUI thingy - I've never looked or used one.  GUIs on a "server" are a bad idea.

I suspect you will be happier with a Windows solution, provided you are willing to give up all the privacy required just to run Windows10.

BTW, if you need to edit any config files for squid (that is normal), please use **sudoedit** - it is safer than other alternatives.

---

### Post by jbaerboc on 2015-08-28
"2 - if you cannot control port forwarding on the edge router, then you cannot have remote access."

Well that puts the nail in the coffin of that idea. Ah well, thanks for the answer anyway :-).

---

### Post by TheFu on 2015-08-28
In the USA, you can replace the ISP router/modem and manage that control.  I know that for residential cable ISPs, it is the law.

There is another option for remote access - I always want to role my own, but you can use something like teamviewer. Trusting a 3rd party who you are not paying which provides some liability protections ... that just seems wrong to me. If you aren't paying for a service, then YOU ARE THE PRODUCT.  For something like remote access ... that means trusting this 3rd party to be nice and not do whatever they want on your system.

---

