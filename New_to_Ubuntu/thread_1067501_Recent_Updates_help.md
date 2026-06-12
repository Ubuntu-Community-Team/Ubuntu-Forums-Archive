---
title: "Recent Updates help"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-02-11
when i tried to update through the normal methods this morning it wouldn't work for me, after going through update manager it gives me this message
```
W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

then i tried
```
sudo apt-get update
```
and i get this message
```
W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/Release.gpg  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

every so often i get an orange triangle running in my taskbar in place of update manager which tells me my update information is old

anybody else with the same problem or a workaround?

---

### Post by trikster_x on 2009-02-11
Do you have the medibuntu repositories enabled?

---

### Post by Messyhair42 on 2009-02-11
i have no idea, where to i check?

---

### Post by trikster_x on 2009-02-11
Administration >> Software Sources >> Third-Party Software

There should be a check mark next to [http://packages.medibuntu.org/intrepid](http://packages.medibuntu.org/intrepid) free non-free.

---

### Post by Messyhair42 on 2009-02-12
yes the repositories are enabled

---

