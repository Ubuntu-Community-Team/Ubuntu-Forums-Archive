---
title: "Updating ClamTK"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-25
I have just installed ClamAV and ClamTK and everything seems to be in order. But when i open up Clamtk and then click on Help and theN update i am informed that i need to be Root. Does that mean opening a terminal and typing Sudo apt-get update ClamTK?

---

### Post by arochester on 2011-06-25
Nearly.

Just open ClamTK from a Terminal. The command gksudo might be better. Try: gksudo clamtk

When open, update.

---

### Post by Matt__ on 2011-06-25
or just terminal ```
sudo freshclam
```

do you have the [PPA for the latest version](https://launchpad.net/~ubuntu-clamav/+archive/ppa) enabled?

---

### Post by Paqman on 2011-06-25
> **Old-un said:**
> I have just installed ClamAV and ClamTK and everything seems to be in order.

Is there some reason you want to run ClamAV? There are much better antivirus suites available for Linux (eg: Avast, AVG). ClamAV is not very effective.

---

### Post by corncob on 2011-06-25
[http://clamtk.sourceforge.net/faq.html#root_update](http://clamtk.sourceforge.net/faq.html#root_update)

---

### Post by Old-un on 2011-06-25
Thanks for all the help and advice everyone!

---

