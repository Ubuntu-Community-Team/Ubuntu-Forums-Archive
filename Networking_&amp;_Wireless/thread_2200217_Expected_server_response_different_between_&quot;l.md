---
title: "Expected server response different between &quot;localhost&quot; and &quot;127.0.0.1&quot;"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by cdaringe2 on 2014-01-18
Hi all:

I have a copy of [http://www.emoncms.org/](http://www.emoncms.org/) running on my local server.  When I post hypothetical data to it via:
[LIST]
[*][http://localhost/emon/emoncms/input/bulk.json?data=](http://localhost/emon/emoncms/input/bulk.json?data=)[[0,10,223]] it works!  When I post via:
[*][http://127.0.0.1/emon/emoncms/input/bulk.json?data=](http://127.0.0.1/emon/emoncms/input/bulk.json?data=)[[0,10,223]] it doesn't work!  Punching 127.0.0.1 does route me to my server doc root.
[/LIST]
I would expect these two to produce the same res!  Why wouldn't they be?  Looking for some tips!
Thanks,
-Chris

---

