---
title: "Alt + TAB and workspaces are not working"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by NewbieLinuxer on 2011-02-01
I have uninstalled compiz as an attempt to increase my performance a bit, but I lost the Alt + TAB and workspaces functionality, i tried reinstalling compiz over and over through the synaptic but it isn't working. The CompizConfig Settings Manager isn't working either.

Any ideas?

---

### Post by matt_symes on 2011-02-01
Hi

What on earth does "isn't working" mean exactly ?

Open a terminal and type 

```
ccsm
```

Does ccsm start ? Do you get error messges ? Can you set settings ? are those setting not sticking ? A better description would be _really_ helpful here.

Kind regards

---

### Post by NewbieLinuxer on 2011-02-01
I'm sorry if it wasn't clear, i meant the process wouldn't start when clicked from the Preferences menu.
Anyhow
```
nlinux@t-xz-pc:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: libprotobuf.so.5: cannot open shared object file: No such file or directory

```This is the output of "ccsm".
I can't set any settings through the front-end, and I have no idea how to set them through commands.

Later edit:
I got it fixed, seems I had to reinstall libprotobuf with compiz. Weird but it worked.

---

### Post by matt_symes on 2011-02-01
Hi

I think i might have come across a bit sharp. That was not intended. Glad it's fixed.

Kind regards

---

