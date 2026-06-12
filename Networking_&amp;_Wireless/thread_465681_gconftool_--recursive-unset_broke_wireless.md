---
title: "gconftool --recursive-unset broke wireless"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by haloedrain on 2007-06-05
Network manager kept automatically connecting to the wrong network, so I used
> gconftool --recursive-unset /system/networking/wireless/networks/{linksys}
to remove the "linksys" router from the networks list.  Other networks are still in the gconf-editor listing, with key values apparently unaltered, but ever since I have been unable to connect to any wireless network at all, whether they were in the networks list before that or not.  Network manager will see networks and attempt to connect automatically and prompt me for the keyring password, but the connection always times out now.  Does anyone know why this happened and how to fix it?

---

