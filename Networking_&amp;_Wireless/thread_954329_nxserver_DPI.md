---
title: "nxserver DPI"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by emanuel.landeholm on 2008-10-21
I'm using the linux nxserver & windows xp client from nomachine and each time I logon I get a DPI of 75x75, rendering my fonts tiny and hard to read.

Adding
 
```

DefaultXDPI = "100"

```

to /usr/NX/etc/node.cfg has no effect. Is there something else I could do?

I could change the font settings in the GNOME Appearance Preferences but I'd rather not since it would mess up my local desktop.

tia,
Emanuel

---

### Post by kimitake on 2009-10-29
I have encountered the same issue.
node.cfg has AgentExtraOptions, so I added as follow.

AgentExtraOptions = "-dpi 96"

and then it worked.

---

