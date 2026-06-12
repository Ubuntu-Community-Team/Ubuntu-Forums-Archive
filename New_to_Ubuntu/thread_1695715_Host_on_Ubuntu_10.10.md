---
title: "Host on Ubuntu 10.10"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by loke8600 on 2011-02-26
Dear Ubuntu Friends:

I am a new convert to Ubuntu [10.10].  While with windows i used Host file "to block ads, banners, 3rd party Cookies, 3rd party page counters, web bugs, and even most hijackers."[as mentioned in mvps.org site]

I wish to do the same in Ubuntu 10.10.  There was an article about this in the forum but it referred to an older version of Ubuntu where host file was not split into host.allow and host.deny.

Please guide me.  Just want to copy the contents of host file from mvps.org to Ubuntu hosts.

I am already using browser extensions - no-script, ghostery, ad block plus.  

thank you for your time.

Regards,

---

### Post by Screenshot on 2011-02-26
On Ubuntu the host file is: /etc/hosts
There you can map a domain to an IP (eg to 127.0.0.1 to "block" something) like on Windows.

Is this what you want to do?

---

### Post by loke8600 on 2011-02-26
[LEFT]yes that is exactly what i want to do.  But, in etc/hosts i see

hosts;
host.allow
host.deny

which ones to use ?

thanks for your reply and help.
[/LEFT]

---

### Post by thefasterblueone on 2011-02-26
Just edit the Hosts, here is a [How-to]("http://jaxov.com/2009/09/how-to-block-websites-in-ubuntu-linux/").

---

