---
title: "Partition Question"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Bcmccmmnx on 2010-11-20
When I use Disk Usage Analyzer, it tells me I have 1.2 TB of available space. The hard drive I installed it on is a 160 GB. There is also a 1 TB external drive connected via USB, and a 160 GB drive with Windows Vista installed. When I installed Ubuntu, I specified that it would be on the 160 GB with nothing on it. Will it ever attempt to write to the other drives without me wanting it to?

Yes, I am an absolute noob, but I am somewhat concerned over what it says.

EDIT: I tried removing the usb drive, and restarting, and now it says it has 140.7 GB available. Huh, maybe it simply saw the external as a possibe place to put data, or what?

---

### Post by Hippytaff on 2010-11-20
Open a terminal (CTRL+ALT+T) and try
```

df -h

```should clarify things a bit :-)

Welcome btw :-)

---

### Post by Rubi1200 on 2010-11-20
+1 to Hippytaff's suggestion.

However, I have noticed that if an external drive is plugged in, Disk Usage Analyzer tends to default to showing the free space on said drive.

---

### Post by matt_symes on 2010-11-20
Hi

> Will it ever attempt to write to the other drives without me wanting it to?

No.

Kind regards

---

