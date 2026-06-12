---
title: "Deja Dup can't find backup files"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by loren41 on 2011-07-08
Running Deja Dup in Ubuntu 11.04.  Deja Dup Restore can't locate backup.

Trying duplicity command it says it can't find file,
duplicity-file.20110216T153127Z.manifest.  When I list the directory, the file is there, but has a .gpg extension added.

The command used was - 
  duplicity --gio --no-encryption file:///home/loren /tmp/restore

Any suggestions?

---

### Post by loren41 on 2011-07-16
> **loren41 said:**
> Running Deja Dup in Ubuntu 11.04.  Deja Dup Restore can't locate backup.

Trying duplicity command it says it can't find file,
duplicity-file.20110216T153127Z.manifest.  When I list the directory, the file is there, but has a .gpg extension added.

The command used was - 
  duplicity --gio --no-encryption file:///home/loren /tmp/restore

Any suggestions?

Also tried reloading Deja Dup and set preferences to a local file folder.  Selected full backup, but same message came back saying the manifest file is missing.

---

