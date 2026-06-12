---
title: "Archived Files"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by newport_j on 2010-05-12
In Ubuntu 8.04 are archived file lettered in red? if an archived files is not in red then using chmod how do I make it red?

Newport_j

---

### Post by anglican on 2010-05-12
> **newport_j said:**
> In Ubuntu 8.04 are archived file lettered in red? if an archived files is not in red then using chmod how do I make it red?

Newport_j
In short, you don't, as  chmod only affects permissions on a file which may be read/write/execute for owner/group/world and has no effect on the colours you see when you list them. The shell appears to use the file extension e.g. .zip or .tar to determine that a file is an archive.

H

---

