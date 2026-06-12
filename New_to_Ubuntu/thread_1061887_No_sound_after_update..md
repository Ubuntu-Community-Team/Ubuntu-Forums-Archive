---
title: "No sound after update."
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Samppa on 2009-02-06
I got this message during the update.

E: linux-restricted-modules-2.6.27-11-generic: subprocess post-installation script returned error exit status 139
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

Now my sound does not work.

I have already tried reinstalling the updates but i just get the same error message.

How do i fix this?

---

### Post by taseedorf on 2009-02-06
well...try

sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure

---

