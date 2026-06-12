---
title: "Failed to execute child process &quot;GameStart&quot; (No such file or directory)"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by beew on 2010-10-04
I have installed the package Robot3D simulator but it doesn't start. When clicking the launcher I got the error message above. I checked the command for the launcher, it is

> GameStart Robot3D %u

I wonder if there is a way to fix this.

I tried running Robot3D in the terminal and it returned 'command not found'. I looked up the files installed from the package from Synaptic and it appears that there is no file installed in /usr/bin or /usr/local/bin where executables usually end up, instead all the files are in /usr/lib with the extension .so

I would appreciate any hint or suggestion, thanks.

---

### Post by NightwishFan on 2010-10-05
How did you install this program and what is the package name? If it is an official Ubuntu program in the repositories you should file a bug. If not, I will do some poking around for you.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by beew on 2010-10-05
Hi, 

I installed it from this PPA on launchpad

[https://launchpad.net/~robot3d-team/+archive/ppa-robot3d]("https://launchpad.net/~robot3d-team/+archive/ppa-robot3d")

The package is not in the Ubuntu repo.

Thanks.

---

### Post by NightwishFan on 2010-10-05
I would contact the maintainer for support. It seems like a well maintained repository though. I am unable to test the packages as I am on Maverick.

---

