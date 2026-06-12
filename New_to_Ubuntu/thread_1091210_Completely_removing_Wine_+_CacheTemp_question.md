---
title: "Completely removing Wine + Cache/Temp question"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-09
Hey guys,
I need to scrape wine COMPLETELY off my system.
Just wondering where all it's folders are, because Synaptic complete removal doesn't rid them all...

My issue is when I go to "Browse C:/" from the Wine menu, nothing opens.

I've tried re-installing it, and the issue stays still.

Also, when I go to reinstall it from Synaptic Package Manager, it already has the files stored in cache or temp folder.

How do I remove this also, so that when I go to reinstall wine, it downloads it again?

Summing up all this...I need wine off my system, and I need to know how to clear temporary files for Synaptic Package Manager/Ubuntu.

---

### Post by yeats on 2009-03-09
Try:

```
sudo apt-get purge wine
sudo apt-get autoclean
```

Then try reinstalling.  The other thing to know is that wine uses a hidden directory in your home folder called .wine, which you might want to delete, but beware that any data you need to keep would be in that folder as well.

Hope that helps.

---

### Post by Gp. on 2009-03-09
Hi,
This did not solve the problem unfortunately.

Also, when I went to re-install, it did not re-download wine.

How do I clear the package manager cache?

---

