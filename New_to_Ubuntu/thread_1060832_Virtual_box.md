---
title: "Virtual box"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Binny88 on 2009-02-05
I have been using Hardy Heron after I upgraded from gutsy.I wanted to install Virtual Box . I installed it from add/remove applications. After I started it it gave me an error message saying that it needed some kernel  modules to work. I installed them from synaptic and restarted the computer and to my horror I discovered that I had got a kernel upgrade . My Nvidia drivers failed to work and the whole screen looked messy. Finally I downgraded to Gutsy.

What went wrong? I also got the same msg in gutsy but VB ran perfectly in Intrepid.

Thanks in advance

---

### Post by Voland on 2009-02-05
You need to recompile kernel modules of VB and nVidia for new kernel. In Intrepid you can use DKMS, so they are compiled automatically.

---

### Post by Binny88 on 2009-02-05
Thanks for your help  Voland.

---

### Post by Voland on 2009-02-05
You are welcome :)

---

