---
title: "How to change proxy settings on ubuntu server?"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by charbo on 2007-06-21
Hi all,

I just installed ubuntu 6.06 server, and during the installation, I put wrong proxy information.
Now I need to reconfigure the http proxy configuration, so I can update the server.

I don't know how to do this. I tried to find out on the google, but all I get is how to set up proxy server.

Can somebody help?

Thank you,

---

### Post by charbo on 2007-06-21
Hi,

I am responding to myself, so others may refer.
proxy setting is controlled by the environment variable.

In my case, I need to set the http proxy to right address, so I would type

http_proxy=http://username:password@host:port/

to generate the environment variable with appropriate proxy server information.
Export the environment variable by

export http_proxy

Doing this as root or add sudo in front should set the system wide proxy setting, I think.
And if you want this reflected every time you boot the machine, you can certainly put these lines in /etc/profile or /etc/bashrc, I think.

Thank you for your attention.

---

### Post by erat123 on 2008-07-11
Thanks for the research charbo!  I just had the same problem and you helped me out.

---

