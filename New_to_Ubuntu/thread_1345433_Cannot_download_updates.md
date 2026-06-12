---
title: "Cannot download updates"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Dinu. on 2009-12-04
E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

whenever i start my updates error msq appered how can i slove this problem

---

### Post by Metallion on 2009-12-04
Could you attach or post the contents of /var/log/apt please?

Also 2 quick checks. You're root partition does have free space left right? Does the problem also occur when typing sudo aptitude safe-upgrade?

---

