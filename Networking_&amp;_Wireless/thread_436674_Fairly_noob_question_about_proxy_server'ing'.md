---
title: "Fairly noob question about proxy server'ing'"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by deva on 2007-05-08
Basically I'd like to have a proxy server on my network purely to save on downloads, so and so that frequently accessed webpages, etc are quicker to download.

Now I'd like to know if this is at all possible.
I'm using Ubuntu 7.04 Desktop

My network is setup as:

Wireless router into gigabit switch.
then switch out to all computers (6 in total, plus 1 on wireless)

sorry for the noobiness. All i've learnt so far is that squid can be used as a proxy server. 

i ONLY want this proxy server to store content for download saving and quicker access.

is this at all doable?

sorry if that doesn't make any sense, if there is anything else that is needed to be known please ask. :)

thanks,

deva.

---

### Post by .rdg on 2007-05-08
Hi,

  you should set up squid on the pc you wish to serve as proxy and then just enter the settings to your other machines. The squid.conf file is really well documented, so you should be fine when going through it. If you want to just save on bandwidth not much has to be changed (or nothing at all really - but be sure to browse through the config file). Remember that the proxy server would have to be up when others try to reach the web or they would have to disable proxy in application settings otherwise.

Regards,
.rdg

---

