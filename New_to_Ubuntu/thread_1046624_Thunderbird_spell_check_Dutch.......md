---
title: "Thunderbird spell check Dutch......"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Dutch on 2009-01-21
Downloaded==> woordenboek_nederlands-2.1.1-fx+tb+sm.xpi

Unpacked it:
**dictionaries**
with **nl.dic** and **nl.aff**

Where should I put which file to use the Dutch spell check ?

Thanks,

Paul.
BTW I'v downloaded Thunderbird itself on a USB stick
and installed it.
It's probably installed on the HD, but don't know where.
Thunderbird 1 and Thunderbird 2 are both running with no problemo's.

---

### Post by Michael.Godawski on 2009-01-21
hi,

try this command to find the installed files:

```
dpkg -L nameofpackage
```

I don't know exactly if this helps you but once I installed the myspell and hunspell packages from synaptic for my second language (German) the spell check also works in other applications like messengers and such.

So perhaps just search for the myspell and hunspell-dk (hope that is right) via Synaptics.

---

