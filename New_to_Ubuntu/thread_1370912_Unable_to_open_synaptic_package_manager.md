---
title: "Unable to open synaptic package manager"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by klandwehr on 2010-01-02
when trying to open up the synaptic package manager I get the following error   
E: Malformed line 1 in source list /etc/apt/sources.list.d/nvidia-vdpau-ppa-karmic.list (URI)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
Please help
:confused:

---

### Post by Zeedok on 2010-01-02
Try editing your sources.list.

At the terminal type:
```

gksudo gedit /etc/apt/sources.list
```

enter your password.

Put two hash signs, ie "##" in front of the lines mentioned in the error message - this "comments" them out - they won't be deleted, they'll just be ignored.  Save the file and try Synaptic again.

---

### Post by 3rdalbum on 2010-01-02
> **klandwehr said:**
> 
E: Malformed line 1 in source list /etc/apt/sources.list.d/nvidia-vdpau-ppa-karmic.list

Line 1 of the file '/etc/apt/sources.list.d/nvidia-vdpau-ppa-karmic.list' could not be understood by the package management system. Either remove this file and try adding the PPA again, or take a look at the file and see if you can correct whatever the problem is.

---

### Post by 3rdalbum on 2010-01-02
> **Zeedok said:**
> Try editing your sources.list.

At the terminal type:
```

gksudo gedit /etc/apt/sources.list
```

enter your password.

Put two hash signs, ie "##" in front of the lines mentioned in the error message - this "comments" them out - they won't be deleted, they'll just be ignored.  Save the file and try Synaptic again.

Not going to help, it's not in sources.list; it's in a different file.

---

