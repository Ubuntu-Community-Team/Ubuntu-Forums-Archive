---
title: "Monitor online/offline status"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by podollb on 2008-01-28
I was wondering if there is a script available to monitor (and possibly graph or summarize) the online/offline status of my server. With that being said, I've written something crude in the past to do this, but I figured I better ask to see if there was something already available. I know my DSL occasionally goes offline, but usually for short time spans, but it would be neat to have this "monitored" every 30 minutes or so to see how often it really occurs. I know it's a simple ping to some remote host, but like I said I figured I'd ask...

---

### Post by joeinnes on 2008-01-29
Google might know. Alternatively

```
#!/bin/bash
#Script to check server uptime
while [ 1 = 1 ]; do ping -c 2 google.com > ~/serveruptimelog.log; sleep 1800; done
 
```

Then search for "100% packet loss" in the log, and note the frequency of occurence.

Joe

N.B. the script above does not terminate, due to the condition 1 = 1. If you need to terminate it, hit ctrl + c while it's sleeping.

---

### Post by podollb on 2008-01-29
Thanks! And yes I tried google but didn't find anything. My original script was done in Perl and it hit whatismyip.org to grab my ip and I logged that to a file and then rechecked every x minutes to determine if that had changed or was not available, that way I would only "log" when necessary.

---

