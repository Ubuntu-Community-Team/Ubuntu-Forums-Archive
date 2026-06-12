---
title: "Cannot change user password"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Geraba on 2009-11-27
I had changed it once, via System->Admin->Users and groups, it changed fine. I think after the kernel update a few days ago this must have happened.

I decided to change it again a couple days ago, and I did the same thing. It confirms that my pass was changed, but when I do anything that requires my password (like updating Ubuntu, sudo...), my new password doesn't work... Only my old one.

I managed to change it via System->Prefs->About me.

Is it a bug?

Thanks in advance.

---

### Post by t0p on 2009-11-27
That's strange.

You can change your password by opening a terminal and typing in:

```
passwd
```

Type in old password and new password when prompted.  When you type in the passwords, you won't see anything appear in the terminal (no letters or asterisks) - that's perfectly fine.  Just type in the passwords as prompted and hit the <Enter> key.

---

### Post by Geraba on 2009-11-27
I was going to try that, but then About Me worked...
I guess this is a bug, why System>Admin>Users and Groups GUI doesn't work?

---

