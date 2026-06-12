---
title: "Message during boot. Significance?"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by Cycledoc on 2010-12-02
Using an old Dell 2650, Ubuntu 10.10 (Maverick)

Have noted the following during boot.  System otherwise does what I want it to.  

[INDENT]23.872206] [drm] nouveau 0000:01:00.0: 0xB720: Failed parsing init table opcode: INIT_CONFIGURE_PREINIT -19
23.872332] [drm] nouveau 0000:01:00.0: 0xB7AA: Failed parsing init table opcode: INIT_CONFIGURE_CLK -19
23.872417] [drm] nouveau 0000:01:00.0: 0xB7CF: Failed parsing init table opcode: INIT_CONFIGURE_MEM -19[/INDENT]

Any ides what this means?  Need a fix?

Thanks

---

### Post by NCLI on 2010-12-02
> **Cycledoc said:**
> Using an old Dell 2650, Ubuntu 10.10 (Maverick)

Have noted the following during boot.  System otherwise does what I want it to.  

[INDENT]23.872206] [drm] nouveau 0000:01:00.0: 0xB720: Failed parsing init table opcode: INIT_CONFIGURE_PREINIT -19
23.872332] [drm] nouveau 0000:01:00.0: 0xB7AA: Failed parsing init table opcode: INIT_CONFIGURE_CLK -19
23.872417] [drm] nouveau 0000:01:00.0: 0xB7CF: Failed parsing init table opcode: INIT_CONFIGURE_MEM -19[/INDENT]

Any ides what this means?  Need a fix?

Thanks
If you don't have any problems, don't bother. It looks like it's nothing to worry about.

---

### Post by wojox on 2010-12-02
It's a kernel bug. Believe their working on it.

---

### Post by Cycledoc on 2010-12-02
Thanks

---

