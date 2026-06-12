---
title: "The following signatures were invalid:"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by robtotheb on 2009-07-04
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Any ideas how to fix this?

---

### Post by Pro-reason on 2009-07-05
I may be getting the wrong end of the stick here, but I think that this (entered on the command line) might fix it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
```

---

