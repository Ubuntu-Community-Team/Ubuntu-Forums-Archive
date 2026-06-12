---
title: "linuxdc limit in filesize"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by sheazar on 2008-03-28
I recently installed linuxdc++ via apt and I've now encountered a problem, when trying to download files larger than 4 GiB I get the errormessage "Begränsning av filstorlek överskriden (core dumped)" In english it translate to somthing like: "Filesize limit exceeded (core dumped)" and the program shuts down. Any ideas why this is happening and how to solve it.

ulimit -a gives the result:
```
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 8182
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 8182
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

### Post by stevensheehy on 2008-04-02
> **sheazar said:**
> I recently installed linuxdc++ via apt and I've now encountered a problem, when trying to download files larger than 4 GiB I get the errormessage "Begränsning av filstorlek överskriden (core dumped)" In english it translate to somthing like: "Filesize limit exceeded (core dumped)" and the program shuts down. Any ideas why this is happening and how to solve it.

ulimit -a gives the result:


What filesystem are you using? Some filesystems like FAT32 do not support files greater than 4GB. LinuxDC++ is compiled with '-D_FILE_OFFSET_BITS=64' so it should be able to create files > 4GB no problem.

---

