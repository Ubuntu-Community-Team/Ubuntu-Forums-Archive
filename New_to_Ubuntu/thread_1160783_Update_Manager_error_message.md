---
title: "Update Manager error message"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-05-16
I was in the middle of updating Ubuntu 8.04 with the Update Manager and then my machine lost power. I rebooted and then tried to finish the update/install. All the files had successfully downloaded. When I clicked Install Updates. I got an error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I opened a terminal session and typed in: ppkg --configure -a

And got message: dpkg: requested operation requires superuser privilege

Can someone tell me how to get super user privilege? Thanks

---

### Post by 123456789123456789123456 on 2009-05-16
type the following in terminal

sudo dpkg --configure -a

after you do that it will ask for your password
this should work

the command sudo gives you the ability to run commands as root aka super uesr

---

### Post by jwaclawsky on 2009-05-16
Thanks I did as you suggested and part of the output messages indicated that "pciutils" was in an inconsistent state and proceeded to process further for some time. It appeared to complete successfully (and indicating that pciutils was the only problem it found). It must of fixed it because when I went to the package manager he said there were 0 broken packages. So I installed the updates and it looks like everything is working. Thanks!

---

