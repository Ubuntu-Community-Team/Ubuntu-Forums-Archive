---
title: "Is /etc/kernel/postinst.d/nvidia-common Important?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by RATM_Owns on 2008-12-07
/etc/kernel/postinst.d/nvidia-common was giving me trouble when installing new kernels from KernelCheck or Master Kernel thread.

So I moved it into /usr/src just for a place for it to be. :P

It's contents were:
```
#!/bin/bash -e
. /usr/share/debconf/confmodule
db_set nvidia-common/obsolete-driver false
db_input high nvidia-common/obsolete-driver || true

if [ -x /usr/bin/nvidia-detector ]; then
    LATEST=$(nvidia-detector)
    if [ ${LATEST} != "none" ]; then
        db_fset nvidia-common/obsolete-driver seen false
        db_subst nvidia-common/obsolete-driver latest $LATEST
        db_input high nvidia-common/obsolete-driver || true
        db_go || true
    fi
fi
```

---

