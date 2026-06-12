---
title: "Unclean shutdown, fsck exit status 4?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by WiseMaturin on 2009-03-08
So my comp shuts down like normal, and when I go to reboot it says "Unclean shutdown" and starts trying to check the drive and stops at 64%, then enters a screen trying to fix the problem.

Then it tells me it's entering a shell, and I have to run fsck manually, and to repair the inconsistency manually.
I am quite sure I do not know how to do that myself, or where to even begin.
But it let's me ctrl+D to boot normally, and it has worked so far.


[B]*]How can I fix it, or at least stop it from trying to check the drives since that takes so much time for it to realize it's not going to work?*[/B


This is like the 20th problem I've had with (k)ubuntu in the last two weeks, maybe a month. I'm not really sure I want to keep dealing with this kind of stuff though, so I might switch back to something a little more stable.

---

### Post by philinux on 2009-03-08
Let it boot and fail. Then issue this command

```
fsck -v
```

If it offers to fix any errors hit the Y key.

---

### Post by WiseMaturin on 2009-03-10
Will do, and report any abnormalities I incur along the way, assuming my computer doesn't catch fire or something.

---

### Post by WiseMaturin on 2009-03-23
So yeah, still misbehaving. I'll try running "fsck -v" again, and maybe that'll show it. If not, then I guess it's back to the drawing board.

---

