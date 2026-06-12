---
title: "Disk Consistency Check Message/Error"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by jenkshacker on 2010-05-26
I recently started dual-booting between Windows 7 and Ubuntu 10.04. Since I installed Ubuntu, I get a message that says that my disk needs to be checked for consistency when booting to Windows 7. I think that I know why, and I skipped it. Is there any way to disable the message *without* waiting for it to check my disk (and possibly "fixing" Ubuntu by removing it)?

---

### Post by frostschutz on 2010-05-26
If you resized the Windows 7 partition during the Ubuntu install, one consistency check run by Windows is required, expected, normal. This is due to the limited NTFS support from Linux side, ntfs-resize marks the filesystem as unclean so Windows can look over it and check that all is ok once.

---

### Post by jenkshacker on 2010-05-26
> **frostschutz said:**
> If you resized the Windows 7 partition during the Ubuntu install, one consistency check run by Windows is required, expected, normal. This is due to the limited NTFS support from Linux side, ntfs-resize marks the filesystem as unclean so Windows can look over it and check that all is ok once.
But do I have to worry about it removing my ext4 partition or rendering it unusable?

---

