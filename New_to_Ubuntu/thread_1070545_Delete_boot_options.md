---
title: "Delete boot options"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Doug11 on 2009-02-15
I installed a set of headers by accident that I don't need. I went into synaptic and uninstalled from there but they still show in the boot menu. How can I remove these?

---

### Post by ajgreeny on 2009-02-15
Headers?  Just headers on their own, or did you also install another kernel, as that is what would show in your grub menu, I think, and if you have the kernel, you may also need the headers as well.  Can you clarify the situation exactly, please.  Look in synaptic > File > History to see exactly what you installed if you can't remember.

---

### Post by Paqman on 2009-02-15
The right file to remove through Synaptic is the "linux-image" one, can you confirm that you uninstalled that one? If you did, it *should* clean up the Grub list correctly.

---

### Post by Doug11 on 2009-02-15
Thanks,,i went and checked the history and the linux image was still installed,,removed it through terminal.

---

