---
title: "Grub Messed UP"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by johnfarrow on 2009-10-22
[B][SIZE=4]Was doing a dual boot and wanted to change it to make XP load first.  Downloaded a program recommended here on this forum and ran it.
     Now it won't boot into Ubuntu.  I get the message "Unrecognized device string"

If I press "E", I can edit.  Is there anything I can do to get Ubuntu back.?
[/SIZE][/B]

---

### Post by drs305 on 2009-10-22
Double post. See next.

---

### Post by drs305 on 2009-10-22
> **johnfarrow said:**
> [B][SIZE=4]Was doing a dual boot and wanted to change it to make XP load first.  Downloaded a program recommended here on this forum and ran it.
     Now it won't boot into Ubuntu.  I get the message "Unrecognized device string"

If I press "E", I can edit.  Is there anything I can do to get Ubuntu back.?
[/SIZE][/B]

One possiblity:

At the error message hit escape. That should put the entry highlighted. At that point, press "e",then "e" again until you get to the line that starts with "root" and has your UUID.  Use the cursor keys and change "root" to "uuid" then boot ("b").

That should get you into the system. Then manually edit grub's menu.lst to make the change permanent.

If that isn't the problem, getting into the boot menu should help you recognize the problem. The message means there is something on one of the lines that Grub doesn't like.

---

### Post by ranch hand on 2009-10-22
Cooling it with the large font would be a real good first step.

Giving some real information would be a second step that I wouldd recommend.

What Ubuntu are you running?  On what?

When did you install XP and the mystery flavor and install them?

What drives and partitions are they on?

Are you using grub-legacy or grub2?

What program?

---

### Post by johnfarrow on 2009-10-22
Hey Thanks a million.  That worked.  Now what should I  change so it wont happen again?

I salute your knowledge

---

### Post by drs305 on 2009-10-22
> **johnfarrow said:**
> Hey Thanks a million.  That worked.  Now what should I  change so it wont happen again?

I salute your knowledge

Well, we still don't really know what you are using, but I suspect Grub legacy.

Open menu.lst as root:
```

gksu gedit /boot/grub/menu.lst

```

Go to all the entries and any that start with "root" change to "uuid" just as you did on the command line.

---

### Post by johnfarrow on 2009-10-22
Thanks for your help drs305.  I really appreciate it.  Now how do I make it SOLVED?

---

### Post by drs305 on 2009-10-22
> **johnfarrow said:**
> Thanks for your help drs305.  I really appreciate it.  Now how do I make it SOLVED?

Glad you got it sorted out.

At the top right of the first post, click on Thread Tools, then mark solved.

---

