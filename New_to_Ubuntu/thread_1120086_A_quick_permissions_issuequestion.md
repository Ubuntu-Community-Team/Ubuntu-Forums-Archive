---
title: "A quick permissions issue/question"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by jeff00z28 on 2009-04-08
in the past on older version i was able to chmod +wr and allow myself to write to the WWW directory. It now won't do that, i need to enable all permissions for the regular user account. I am trying to implement help desk software that runs as a web server. I just need to copy the files to the www folder but It will not allow me to. thanks.

---

### Post by BslBryan on 2009-04-08
Try ```
sudo chmod o+wx
```

It worked for me.  :-)

---

