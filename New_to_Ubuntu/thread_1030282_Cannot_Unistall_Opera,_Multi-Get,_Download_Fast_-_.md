---
title: "Cannot Unistall Opera, Multi-Get, Download Fast - help please???"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Dynamite Jammy on 2009-01-04
Hello,

I was having some problems with flashget on firefox so thought i'd try out a combo of

opera
multi-get
downloadfast

Which someone on another thread recommended as an alternative


I installed these - had the same problem i had with firefox and decided to unistall them

Unfortunately, when I go to applications/and and remove

None of the three come up in the list of installed applications, so I cannot select them to uninstall.

Anyone have any ideas why this is please?

Thanks in advance

---

### Post by tad1073 on 2009-01-04
```
whereis opera
whereis multi-get
whereis downloadfast
```

you will have to acquire root privileges to delete the corresponding files.

or you can,

```
sudo rm /path/to/opera
```

etc.

---

