---
title: "How to use separate home partition on new install?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by cyan on 2009-02-24
I have Home set up on a separate partition and may change the existing distro to something else. Currently running Easy Peasy but may switch to vanilla Ubuntu or EEEbuntu.

In order to keep all my settings and have access to my files on the separate home partition, is it as simple as pointing to that separate Home partition during install and NOT putting a check in the "Format?" box? Will this use my existing Home or will it create a new set of folders (documents, photos, etc) alongside my Home folders from the earlier install?

I hope I'm making sense, here. I am a Gnu/Linux noob and just trying to save myself from doing too much harm. 

Thank you!

---

### Post by halitech on 2009-02-24
when you are doing the install, select manual partitioning, set up the rest of the partitions and make sure you mount /home correctly and select to not format. This *should* save your /home folder.

---

### Post by cyan on 2009-02-24
Puurrrfect. That's what I needed to know. Thank you so much for the help!

---

### Post by taurus on 2009-02-24
If you switch from one distro to another, you have to be real careful about using the same $HOME.  Some distros will assign the first user with UID of 500 while Ubuntu uses 1000.  And if both distros use 1000, then make sure you use the same login name when you create one.  Just keep that in mind.

---

### Post by cyan on 2009-02-24
Will following Halitech's advice to make sure you mount the correct /Home take care of this issue?

---

### Post by halitech on 2009-02-24
no it won't

---

### Post by cyan on 2009-02-24
Thanks, Halitech. Does that mean that using the same login name on Ubuntu installs should take care of the problem but any install with uid500 will be a problem?

I guess two questions come up for me. First, how would I know if this was to be a problem? Just research the particular distro I want to install? And, assuming I figure out I'm going to have a problem, how would I go about resolving it?

Thanks again for all the help!

---

### Post by taurus on 2009-02-24
Boot from the LiveCD.  Then mount the partition of your /home and have a look to see which value it uses.

---

### Post by cyan on 2009-02-24
Ah, good advice. Thank you, I'll try that.

---

