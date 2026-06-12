---
title: "rsync log format"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by node2network on 2011-07-06
I'm not good at English.

I know rsync has option to increase verbosity. But this option has much information.
I want to only know which file is updated. How do I set an options?
My option is below. 
$ rsync -auz --delete source_direcotry destination_directory

---

### Post by seawolf167 on 2011-07-07
If you add the *-v* switch, you will be able to see what files are being deleted (from the *--delete* switch), and transferred/updated (from the *-u* and *-a* switches)

So, try

```
rsync -auzv --delete /source /destination
```

---

