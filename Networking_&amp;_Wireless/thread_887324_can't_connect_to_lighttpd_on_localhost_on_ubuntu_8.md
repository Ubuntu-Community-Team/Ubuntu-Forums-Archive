---
title: "can't connect to lighttpd on localhost on ubuntu 8.04"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by dhoss on 2008-08-12
Hi everybody,

I've gone through about every plausible cause that might be the source of this error, and nothing has turned up.

I'm attempting to run lighttpd as a development server on my Compaq Evo N610c running Ubuntu 8.04 (originally installed Kubuntu 8.04 but downloaded the ubuntu-desktop package(s) and switched to GNOME to fix my wireless issues I was having.) and when I load up firefox and go to [http://localhost](http://localhost), it attempts to load for a while then times out.  Pinging localhost on any port (as well as telnet-ing) seems to all yield the same time out.

I can't figure this out.  My /etc/hosts file looks like this: 
> 127.0.0.1 localhost.localdomain localhost devin-laptop


I think I've done my due diligence but if something is missing on my end please don't hesitate to let me know.

Thanks,

-dhoss

**Solved:** For some reason lo was down, so I just did sudo ifconfig lo up and things worked.

---

