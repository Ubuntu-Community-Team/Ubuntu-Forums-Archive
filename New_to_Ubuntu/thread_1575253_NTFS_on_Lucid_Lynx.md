---
title: "NTFS on Lucid Lynx"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Scifer on 2010-09-15
I'd like to know how is NTFS support under Lucid Lynx.

[LIST]
[*]Does it have full write support?
[*]Do I need to install any driver or tools?
[*]Does it generate too much corruption?
[*]Any advice?
[/LIST]

---

### Post by Scifer on 2010-09-15
[LIST]
[*]Is it's permissions system like linux's file systems?
[*]Is it safe to use a NTFS partition as home directory?
[*]Does NTFS make files vulnerable to Window$ viruses?
[/LIST]

---

### Post by sikander3786 on 2010-09-15
NTFS-3g is the driver and it has now developed to be a pretty solid and reliable driver for NTFS under Linux. One can now safely say that Linux nearly natively supports NTFS :-)

The easiest way is to install ntfs-config-tool

```

sudo apt-get install ntfs-config

```

Launch it from System >>> Administration >>> NTFS Config Tool and mount your NTFS partitions accordingly.

Regards.

---

### Post by sikander3786 on 2010-09-15
> **Scifer said:**
> [LIST]
[*]Is it's permissions system like linux's file systems?
[*]Is it safe to use a NTFS partition as home directory?
[*]Does NTFS make files vulnerable to Window$ viruses?
[/LIST]
Its permission system doesn't match Linux one, thats why Linux is more secure and reliable.
You can't use NTFS as home directory because of the permissions issue.
Using NTFS doesn't make your system vulnerable to Window Viruses because the OS (Ubuntu) is resistant to the same.

---

