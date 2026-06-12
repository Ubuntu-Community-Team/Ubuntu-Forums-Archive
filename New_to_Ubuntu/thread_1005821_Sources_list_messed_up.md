---
title: "Sources list messed up"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by mark100net on 2008-12-08
I am getting a bunch of 404 errors when I try to update my sources list, e.g. 

-------

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
-------

Is there an easy way to get an updated list?

Thanks

---

### Post by drs305 on 2008-12-08
Those links are to *Feisty* repositories. *Feisty* reached it's end of life in October so the repositories are most likely no longer available.

If you are still running *Feisty*, consider upgrading. If you are not running feisty, edit your sources.list and remove those entries or change them to your current distro.

---

### Post by mark100net on 2008-12-08
Thanks for your reply.

By upgrading do you mean installing a new distro from a fresh download?

If I try the "upgrade" option in the update interface I get the same errors.

---

### Post by drs305 on 2008-12-08
My recommendation would be to do a clean install of either hardy (LTS) or intrepid. 

Here is a link to the Feisty "End of Life" sticky, which discusses some of your options:
[http://ubuntuforums.org/showthread.php?t=947232]("http://ubuntuforums.org/showthread.php?t=947232")

Since you don't seem to mind sticking to one version for a long period, you might consider moving up to Hardy Heron, the Long Term Support version of ubuntu. The desktop version will be maintained until April 2011. Here is a link for installing Hardy:
[http://ubuntuforums.org/showthread.php?t=849915]("http://ubuntuforums.org/showthread.php?t=849915")

Upgrading can be a hassle but there have been some major improvements since Feisty and once you get it set up I'm sure you will be happy with either Hardy or Intrepid.

---

### Post by bapoumba on 2008-12-09
Just in case, Feisty (and older releases) repos are here:
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

