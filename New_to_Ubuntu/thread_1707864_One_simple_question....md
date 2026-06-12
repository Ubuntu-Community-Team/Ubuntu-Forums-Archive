---
title: "One simple question..."
date: 2011-03-15
forum: New to Ubuntu
---

### Post by jfloydb on 2011-03-15
Can I install Xubuntu as a WUBI install?

If so, allow me one more question: How?

Thanks very much...

---

### Post by hotrod6657 on 2011-03-15
I believe the answer would be yes.

Someone can correct me if I am wrong but I believe you would install Ubuntu like you normally would for a Wubi install, and then search the packet manager for:

```
xubuntu-desktop
```

That should install the needed packages.  When it's done log out and select the xubuntu session (at the bottom of the screen when you select your user name) and it should load the xubuntu desktop environment.

The procedure should be the same as what's outlined here for Kubuntu:

[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by Paqman on 2011-03-15
Yes, I believe Xubuntu is one of the options under "Desktop Environment" in the Wubi installer. You can get the installer [here](http://wubi.sourceforge.net/).

---

### Post by bcbc on 2011-03-16
> **Paqman said:**
> Yes, I believe Xubuntu is one of the options under "Desktop Environment" in the Wubi installer. You can get the installer [here](http://wubi.sourceforge.net/).

Don't use that version. It's 10.04.1 which no longer works (actually never worked for Xubuntu due to a bug). Try here instead: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)  (that's 10.10)

---

### Post by kn0w-b1nary on 2011-03-16
You can also download the Xubuntu 10.10 .iso then un-archive it with MagicISO, then run the extracted "wubi.exe"

---

### Post by hotrod6657 on 2011-03-16
That's good to know.  I was going to suggest just downloading the .iso for xubuntu but I wasn't sure if it had the same wubi.exe as regular ubuntu has.

I think that is a much better way of doing it as you won't end up with all of the extra menu entries for GNOME applications as well.

---

