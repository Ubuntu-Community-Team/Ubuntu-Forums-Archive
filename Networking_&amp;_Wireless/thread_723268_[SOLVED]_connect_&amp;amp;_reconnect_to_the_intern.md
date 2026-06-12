---
title: "[SOLVED] connect &amp;amp; reconnect to the internet"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-03-13
im using an ADSL connection, which was configured at the beginning with 'pppoeconf'.
now when I start Linux , the connection to the internet is established automatically.
Is there any way to disconnect and reconnect again without restarting?

---

### Post by Paris Heng on 2008-03-13
> **StOoZ said:**
> im using an ADSL connection, which was configured at the beginning with 'pppoeconf'.
now when I start Linux , the connection to the internet is established automatically.
Is there any way to disconnect and reconnect again without restarting?

Hope this can help,

To connect:
> #sudo pppoeconf

To see log:
> #plog

To turn on:
> #pon dsl-provider

To turn off:
> #poff

---

### Post by StOoZ on 2008-03-13
thanks!

---

