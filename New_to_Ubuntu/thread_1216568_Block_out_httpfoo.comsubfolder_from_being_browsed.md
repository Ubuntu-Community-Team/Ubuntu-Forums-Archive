---
title: "Block out http://foo.com/subfolder from being browsed"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by hanzj on 2009-07-18
How can I block out a certain URL in the form of [http://foo.com/subfolder](http://foo.com/subfolder) from being browsed on any browser on our computer? We want to block [http://foo.com/subfolder](http://foo.com/subfolder) without blocking c

OpenDNS.com can NOT do this, as it blocks out per domain. Therefore, if we have OpenDNS block out [http://foo.com/subfolder](http://foo.com/subfolder) successfully, it would also block out [http://foo.com](http://foo.com) and [http://foo.com/some_other_subfolder](http://foo.com/some_other_subfolder), which we don't want to have blocked.

Is there some sort of blacklist/whitelist text file that I can create on my ubuntu computer?

Thanks.

---

### Post by t4thfavor on 2009-07-18
There are devices that will let you do this, and firefox has a plugin that will do it. The cheapest method would be to get a transparent proxy (like squid) installed, and set it up to block that dir. The easiest way is to get a hadware device that will give more control over what is happening on your network.

Some examples would be an Untangle(free open source requies an old pc) or a wrt54GL with DD-WRT firmware. They will both let you block any manner of anything from your network.

---

### Post by bodhi.zazen on 2009-07-18
Or dansguardian

---

### Post by hanzj on 2009-07-20
Is there no way to do what I want without installing a new program?
Is there a way to do what I want just by adding a text file somewhere?

---

### Post by OffAxis on 2009-07-20
?
Are you talking about blocking access to that folder from web access or blocking access from other users on the LAN or from other users on your workstation?

---

### Post by hanzj on 2009-07-20
offaxis,
just one computer.
and the folder is on the web. (The folder is not on a private network).

---

