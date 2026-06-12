---
title: "Process example"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by youngfellow on 2010-08-29
hi,
what does it mean by stating that a single program can have multiple processes?
Can anyone give me an example also?
Any help will be greatly appreciated.

---

### Post by papibe on 2010-08-29
Follow this instructions:

Close firefox (and all browsers). Open a terminal:
```
$ ps aux | grep firefox
```
You should see no process (except the grep you're executing). If you see one, wait a few seconds and try again.

Open firefox, open a couple of tabs, go to youtube and play one short video. Then open a terminal:
```
$ ps aux | grep firefox
```

You'll see a couple of firefox process running, and the flashplugin for firefox.

Did it help?
Regards.

---

