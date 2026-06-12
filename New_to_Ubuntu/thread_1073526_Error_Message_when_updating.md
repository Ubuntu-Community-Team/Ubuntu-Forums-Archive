---
title: "Error Message when updating"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by nevabry on 2009-02-18
I get an error message when my Package Manager tries to Update. 




W: Failed to fetch [http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead



Anyone know what this is and how to fix it?

Thanks,
Geneva

---

### Post by drs305 on 2009-02-18
The repository is down. Since it is an unofficial repository I don't know if there are any mirrors that might work (but I doubt it). You can either try it later and/or disable that repository by opening synaptic or software sources and go to Settings > Repositories > Third-Party and untick this specific repository.

---

