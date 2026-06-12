---
title: "Error when trying to install any packages manually..."
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Sava8420 on 2009-05-10
So if I am using Synaptic or Apt-get in terminal I get the error:

 Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

Any help would be greatly appreciated.  I should also mention that I am unable to activate my restricted drivers as the jockey backend crashes but I am thinking it is likely for the same reason???  Am running 9.04 AMD64.

---

### Post by Peter09 on 2009-05-10
Have you tried a reboot to clear any old files?

---

### Post by sharks on 2009-05-10
> **Sava8420 said:**
> So if I am using Synaptic or Apt-get in terminal I get the error:

 Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

.

Thats because that you might have been using both package updaters( installing on synaptic and trying to update on terminal or vice versa). So use one at a time

---

### Post by Partyboi2 on 2009-05-10
> **Sava8420 said:**
> So if I am using Synaptic or Apt-get in terminal I get the error:

 Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)

Any help would be greatly appreciated.  I should also mention that I am unable to activate my restricted drivers as the jockey backend crashes but I am thinking it is likely for the same reason???  Am running 9.04 AMD64.
Hi, make sure you only have one package manager open at a time eg apt-get, dpkg, synaptic, update Manager.

---

### Post by Sava8420 on 2009-05-10
> **Partyboi2 said:**
> Hi, make sure you only have one package manager open at a time eg apt-get, dpkg, synaptic, update Manager.

Ok what if I had attempted to install with the Hardware Drivers prior to using apt-get or synaptic?  Cause I'm pretty sure I've tried that first but it find the drivers then displays it then I click on "activate" and nothing the download window comes up but does nothing.   Let it sit for a while and will show error for jockey backend.  I haven't had the terminal open when in synaptic or vise versa nor have I been using the update manager at the time.

---

### Post by Partyboi2 on 2009-05-10
What is the error message you are getting for jockey backend?

>   Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable) If no package manager is open then check the processes in  case one is still running in the background
```
ps -e
``` If there are any running then kill the process
```
sudo killall name
```
*change name for name of process.

---

