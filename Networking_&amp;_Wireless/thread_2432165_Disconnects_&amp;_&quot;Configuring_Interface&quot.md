---
title: "Disconnects &amp; &quot;Configuring Interface&quot;"
date: 2019-11-28
forum: Networking &amp; Wireless
---

### Post by allen2 on 2019-11-28
Desktop, unsure the wireless card.  It generally runs into problems every 2 hours or so, but it varies greatly.  It suddenly drops the wifi connection and gets stuck "configuring interface".  Normally, I just restart the computer and it is fine (for 40 minutes or less if I'm unlucky :( ).

Today, I decided to run 

sudo netplan apply  (No idea what this command does, not really sure if it's related to the issue.  Mostly just pointing out that the next command does at least temporarily reset the issue.)

sudo systemctl restart NetworkManager.service

And it was able to reconnect without a restart.

Any ideas on what I should do to prevent this issue occuring?  Any lines I should run to trace what's going on?

---

