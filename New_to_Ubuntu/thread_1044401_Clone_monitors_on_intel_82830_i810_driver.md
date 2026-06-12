---
title: "Clone monitors on intel 82830 i810 driver"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Hospadar on 2009-01-19
I have an old tablet machine with an intel 82830 video card using the i810 driver.  I'd like to set it up to clone output to the vga port so I can use it for presentations etc.  How would I go about setting it up so it is always cloning my output to that port. I tried grandr on the off chance it might work, but it did not in fact work.

Thanks,
L-tron

---

### Post by Hospadar on 2009-01-19
Solved it!
Installed "i810switch" from repos, then
```
i810switch crt on
```

---

