---
title: "[SOLVED] Little SMB Problems with Sudo"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by d4v1dv00 on 2008-06-24
Hi there,

I been trying to connect to a Windows Vista shared folder across the network. If I follow the instruction shown [here]("https://help.ubuntu.com/community/SettingUpSamba?highlight=(SMB)#head-89265cdeb3c9eb5e4aca280353cc2a4c69c65537"), everything works fine but there is a little problem with the "sudo" command for everything else in local machine.

For all process that requires "sudo" (e.g. Update manager), the window will just freezed up. After google a little, found that if follow the instruction above (linked), apparently under /etc/hosts the entry of:

```
127.0.0.1     my-laptop
```

has became:

```
127.0.0.1     my-laptop.workgroupname
```

So in order to get sudo work, i need to remove the ".workgroupname". I found this is pretty annoying and although there is been a bug lodged and I am wondering is there any workaround for me in this scenario?

Many thanks

---

### Post by Iowan on 2008-06-24
Ordinarily 127.0.0.1 is named "localhost", 127.0.1.1 is hostname.  I don't remember correct order, but you should be able to have```
127.0.1.1 laptop.workgroup laptop
```

---

### Post by d4v1dv00 on 2008-06-24
Thanks, it works!:popcorn:

---

