---
title: "Can't move home"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by bj218 on 2010-11-21
Why can't I move home to homeu? I have done it in the past but do not seem to be able to do it now! I am having all kinds of problems this is just 1
of them. I just reinstalled ubuntu 9.10 & am trying to get it back to where it was last week!! I think I added 2 attachments to this but I don't where
to look for them.

---

### Post by oldfred on 2010-11-22
This one discusses the issue, but uses rsync.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
The --exclude='/*/.gvfs' prevents rsync from complaining about not being  able to copy .gvfs, but I believe it is optional.  Even if rsync  complains, it will copy everything else anyway.  ([See here for discussion on this]("http://ubuntuforums.org/showthread.php?t=791693"))

---

