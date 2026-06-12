---
title: "Live cd customization and mplayer installionation problems"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-04
I am on the part when Im adding in programs to the edit follow under the sudo chroot edit. When I do apt-get install mplayer I get 

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only have requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdvdnav4 (>= 0.1.10) but it is not installable  
THEN IT saids that about 9 more times with different lib packages(files) and a mplayer-skins package(file).
and then it ends with E: Broken packages.


Anyone got advice am i doing something wrong or is there a different download package name that I can do. The mplayer-doc installed fine.

I also did the apt-get update and apt-get upgrade as well as the medibuntu stuff for media stuff and dl'ed the libdvdcss2 package(file).

---

### Post by ericeclifford on 2009-02-04
when I try to do the apt-get install on the depend packages it couldnt install it saids Package (name) is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package (name) has no installation candidate

---

### Post by ericeclifford on 2009-02-04
been searching and counldnt fight a solution yet and ideas?

---

