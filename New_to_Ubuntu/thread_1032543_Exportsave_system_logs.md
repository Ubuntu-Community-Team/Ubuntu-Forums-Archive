---
title: "Export/save system logs"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by AvWijk on 2009-01-06
As I'm thinking that an useraccount of my Ubuntu server might be abused, I want to copy all the important logs first. Usefull information was given by typing **last** and **lastlog**, but how do I save this to -say- a .txt file?

---

### Post by lykwydchykyn on 2009-01-06
You can use a redirect to send the output to a file, like this:
```

last > output-of-last.txt
lastlog > output-of-lastlog.txt

```

Basically, the ">" character will send the command's output into a file.

Also, you should have log files under /var/log for most things; they are just plain text files (though sometimes the older ones are compressed).

---

### Post by AvWijk on 2009-01-06
Thanks, that's what I needed. When I copied /var/log/last to floppy I ended up with a 280 KB large file which was not readable, so > did the trick.

---

