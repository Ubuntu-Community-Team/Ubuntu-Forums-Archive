---
title: "No Swap in Ram"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by DrMilo on 2009-10-02
Hi all! My Hardy Heron seems to be accessing the hard drive a lot and tonight I was doing some fairly intense work with Open Office and my computer totally bogged down. Well with CPU usage at 100%, System Monitor told me that there was 0 RAM swap going on. That seems wrong to me. What should I do?

Thanks in advance.

---

### Post by sliketymo on 2009-10-02
> **DrMilo said:**
> Hi all! My Hardy Heron seems to be accessing the hard drive a lot and tonight I was doing some fairly intense work with Open Office and my computer totally bogged down. Well with CPU usage at 100%, System Monitor told me that there was 0 RAM swap going on. That seems wrong to me. What should I do?

Thanks in advance.

sudo swapon?:confused:

---

### Post by jocko on 2009-10-02
> **DrMilo said:**
> Hi all! My Hardy Heron seems to be accessing the hard drive a lot and tonight I was doing some fairly intense work with Open Office and my computer totally bogged down. Well with CPU usage at 100%, System Monitor told me that there was 0 RAM swap going on. That seems wrong to me. What should I do?

Thanks in advance.
Swap is only supposed to be used when your ram is getting full, and has nothing to do with cpu usage. When your computer starts to need to use swap you will notice a very serious slow-down as everytime something needs to be loaded into ram, something else needs to be moved from ram to the hard drive (which is a lot slower than ram).
But if you get close to 100% memory usage and still see no swap usage you may have a problem.

If you have 100% cpu usage, that just means that something is using all of your cpu capacity. The system monitor can tell you which process is using your cpu.

---

### Post by DrMilo on 2009-10-02
Fine but what's 'safe'?

---

### Post by jocko on 2009-10-02
> **DrMilo said:**
> Fine but what's 'safe'?
Exactly what do you mean here? What's safe in what respect?

---

### Post by DrMilo on 2009-10-02
> **jocko said:**
> Exactly what do you mean here? What's safe in what respect?

No worries. I've got a handle on it now.

---

