---
title: "DSL not working"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Auria on 2007-03-03
I configured DSL as usual with pppoeconf on Ubuntu Edgy.

I get this:
in file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-eth0-provider-provider'

and it won't connect. The same procedure worked in Dapper (no i did not dist-upgrade :P), and also worked from the Edgy liveCD.

Any advice? Thanks

---

### Post by Auria on 2007-03-03
I fixed it by replacing 'nic-eth0-provider-provider''by 'nic-eth0' after a few random tries. Weird that it doesn't work by default...

---

