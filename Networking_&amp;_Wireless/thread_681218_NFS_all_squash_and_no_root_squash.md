---
title: "NFS all_squash and no_root_squash"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by gansitofrito on 2008-01-28
Hello,

I'm attempting to use the options all_squash and no_root_squash simultaneously (my goal is to have all non-root users squash to a specific group and user id, but have root mapped to root.)  However, all_squash seems to overrule no_root_squash.  Has anybody gotten this to work?

Thanks,
gansitofrito

---

### Post by kidders on 2008-01-30
Hi there,

If you specify "all_squash", then _all_ UIDs are squashed to 65534. The "no_root_squash" directive will continue to do its job, but since no operations will ever be performed with UID 0, it simply has no effect.

Using "no_root_squash" is highly inadvisable anyway (since any user with access to the root account on a client machine would gain root privileges on the server), so I would not suggest using it, to be honest.

---

