---
title: "Ntfs-config problem"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by magedsoft on 2010-12-01
WHEN TYPING IN TERMINAL NTFS-CONFIG :::


root@deadline-G41M-Combo:~# ntfs-config
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'


HOW CAN I SLOVE IT HELP ME

---

### Post by Scoobin on 2010-12-01
That looks to be exactly the same error I'm now having since reinstalling Ubuntu 10.10 just a couple days ago.

---

