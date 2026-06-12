---
title: "NetworkManager with more than one dsl-connection"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by froebi on 2008-09-27
Hi,

I have NetworkManager installed and a DSL-connection configured via pppoeconf, named "dsl-provider". Now I see this in NetworkManager under "Dial-Up Connections->dls-provider". Connecting and Disconnecting works fine.

Now I want to configure a second DSL dial-up connection in the same way. For this I simply copied and adjusted my /etc/ppp/peers/dsl-provider to dsl-provider2. Connecting and disconnecting via dsl-provider2 works fine with pon and poff. But I do not see dsl-provider2 in NetworkManager. -- So how do I tell NetworkManager about dsl-provider2? Is there some kind of config file or such?

Christian

---

