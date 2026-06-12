---
title: "command fsck - should I?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-14
Hi I have an odd issue whereby each time I book my computer the splash screen loads fine etc. The issue is that the OS always wants to give me a systems checking info that lasts for a couple of  minutes.

Each check has <OK>

I was advised to run a "command fsck" - do i do this by typing ```
fsck 
``` into the terminal? When I tired doing this I was told that:

"WARNING"!! Running fsck on a mounted filesystem may cause SEVERE filesystem damage"

Seems dangerous to try but this irratating login issue is becoming annoying...

---

### Post by RomeReactor on 2009-02-14
Hi. Don't run fsck on a mounted partition; if you need to run fsck to correct a filesystem error (for example, if fsck runs automatically at boot and tells you to run it manually), it's better to load the Ubuntu Live CD and use Gparted (using Gparted from the Live CD, right click on your partition and press "Check").

Also, please don't make multiple posts about the same problem; you're getting answers to this problem in your other thread.

---

### Post by listerdl on 2009-02-14
Cool thanks for the info! Sorry for the mix post!

---

