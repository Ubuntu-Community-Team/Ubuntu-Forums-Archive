---
title: "Firefox 3.5.3 will NOT Reboot after addons install"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-18
Hi all!
I just installed the new firefox version, 3.5.3.
I was reinstalling my addons and when I finish installation process, and Firefox ask me to reboot for modifications to take effect, I press reboot bottom on addons install window, Firefox will close but wont reboot.

If I restart Firefox the addons are still there but not installed, and the addons window is again asking to reboot the program.

Any idea?

How do I check in Terminal if each and every Firefox process is stopped when it closes down? Which is the code?

Ty ;)

---

### Post by Soul-Sing on 2009-09-18
> How do I check in Terminal if each and every Firefox process is stopped when it closes down? Which is the code?

```
pkill firefox
```

---

### Post by webwiller on 2009-09-18
That's what I was looking for, tx mate! ;)

---

