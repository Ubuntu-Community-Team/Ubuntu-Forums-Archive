---
title: "Dialup connection timeout after 2.5 minutes"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by kit.regan on 2005-11-14
As a member of the dying race of dialup modem users...

Problem:
Connection drops after 2.5 minutes

Cause:
My ISP does not support LCP echo requests. So the connections times itself out.

Solution:
edit etc\ppp\options and comment out:
#lcp-echo-interval 30
#lcp-echo-failure 4

Plea:

1) Could ubuntu folk makes these the default values or add this comment to the help file.
2) Have gnome ppp or kppp available as default applications to make life for dialup users bearable.

If you want to attact windows users this has to "work out of the box."

---

