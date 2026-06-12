---
title: "Evolution Not Working!"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by cressrt on 2010-02-23
Hope someone can help.  Evolution will not connect.  I closed it last night with no problems it will not load this morning; it justs "sits there" greyed out saying loading.  I can force a quit where it states that it is not responding. I know there was a recent global update but cannot remember if this before or after I closed it down.

---

### Post by cressrt on 2010-02-23
Fixed it, I  did a restart and found an Evoultion reminder not working.

---

### Post by scottuss on 2010-02-23
Just a quick tip: If you want to try an alternative, Thunderbird is a great email client.

---

### Post by gifford.scott on 2010-04-29
I saw this identical issue for Evolution mail after a significant ubuntu 9.10 update that required a system reboot.  After the reboot, Evolution hangs repeatedly on start-up, but allows itself to close down, stating that the evolution process is "not responding".  As mentioned above, if you attempt to reboot again, a window comes up, stating that the 'evolution-alarm-notify' process is still running.

To fix, bring-up the System Monitor by selecting 'System->Administration->System Monitor'.  Click on the Processes tab under System Monitor, and you should see 3 evolution-* processes running, even though you've closed the Evolution application.  You need to end these 3 processes by holding the Ctrl key and selecting all three process lines, then clicking on the 'End Process' button in the lower right of the System Monitor screen.  After killing these processes, you should be able to successfully restart Evolution mail.

---

