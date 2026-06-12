---
title: "blinking netbook no mouse!"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by mikhaell on 2010-05-02
i just installed 10.04 on my netbook (remix). Everything seemed fine until i rebooted and suddenly things stopped working . I can't see the mouse (sometimes it pops up as a blck x) and i don't have access to the sidebar. on top of that, the screen blinks. Any ideas?

---

### Post by mikhaell on 2010-05-02
continued--- I enter "appearance" though gnome do, and change the visual effects- the graphic drivers are checked and then somehow the problem is solved. Unfortunately, when i reboot the problem is renewed.

---

### Post by P4man on 2010-05-02
what videocard do you have in that laptop? If you dont know, open a terminal and type

```
lspci
```

If its an intel 8xx (like i855) then its a known issue. Its in the release notes, those cards dont play nice with lucid. In the release notes there is a link with possible workarounds.

---

### Post by mikhaell on 2010-05-04
thanks. The problem was actually the compiz. i un-installed and everything is fine. Odd because 9.10 worked fine with it. Got any idea as to why this is?

---

