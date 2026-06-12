---
title: "Cannot find/install acroread"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by sunwatcher on 2011-02-24
I cannot seem to find acroread anywhere.  Synaptic gives nothing, nor does "sudo apt-get install acroread" (result is "Unable to locate package acroread").  I went to the Adobe site, but I had trouble there too since I have an AMD Athlon cpu and the Adobe .deb install reported that I have the wrong architecture.  Could it be that having an AMD cpu with Linux prevents one from installing Adobe Acrobat Reader?

---

### Post by jcolyn on 2011-02-24
I just checked in synaptic and it shows up for me.

Try ```
sudo apt-get update
``` then try again..

---

### Post by 3rdalbum on 2011-02-24
1. It's in the Partner repository. You probably need to enable that repository in Synaptic.

---

### Post by sunwatcher on 2011-02-24
Thank you!  Yes, it was in the Partners Repository.  I have just never had to manually add that repository before.  Many thanks.

---

