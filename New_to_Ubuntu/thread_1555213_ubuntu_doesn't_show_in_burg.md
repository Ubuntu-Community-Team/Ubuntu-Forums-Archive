---
title: "ubuntu doesn't show in burg"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by libihero on 2010-08-17
i accidently did something on the burg editor, and now ubuntu doesnt show.  instead, it just shows "linux with linux" and has tux as the icon.  how can i change it back to the ubuntu logo?

---

### Post by stoogiebuncho on 2010-08-17
I believe the file responsible for naming your linux entries is /etc/burg.d/10_linux

I'm not sure how much you like getting your hands dirty - editing that file is a little bit involved, but if you take your time and read through it you will probably be able to figure out what's going on even if you don't do a lot of scripting.

If you want to reset it back to it's original, you can either reinstall burg, or you can grab the file /etc/grub.d/10_linux and copy it over to your /etc/burg.d/ directory.

Have you been editing the conf files by hand, or have you been using the Burg-manager?  I've found that Burg-manager doesn't always do what it's supposed to, and I've had it totally wipe configuration files before, which might be what happened to you.

---

