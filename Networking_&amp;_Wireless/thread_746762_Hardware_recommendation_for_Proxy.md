---
title: "Hardware recommendation for Proxy"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by john.burdell on 2008-04-05
I've got a good friend of mine who is in China at the moment
and asked me last year to let me proxy his traffic through a
machine on my home network.

I just put Linux on an old box and setup port forwarding on
my router to let him login via ssh and then he tunnels his traffic
so that everything appears to come from my home connection.
(In addition to the Great Firewall of China, apparently, he can't
login to his online banking or credit card account from China
without flags being raised on his accounts.)

I would like to continue to let my friend use my home connection,
but was wondering if it was possible to do this using a Linksys
WRT-54G?  The old box I'm currently letting him use is old and
I think uses a fair amount of power and I'd like to cut down my
electric bill as much as possible.

If anybody has any other suggestions, they'd also be appreciated.

Thanks,

John

---

### Post by kevdog on 2008-04-05
Yes this is possible by flashing your Linksys WRT54G with the dd-wrt firmware.  It has a build in ssh daemon that you can activate.  Also you can choose to upload his public key if you want to connect using rsa keys over a password.

You only then need to leave the router on full time -- it probably is anyway -- instead of your computer -- and much more stable if you ask me!

---

