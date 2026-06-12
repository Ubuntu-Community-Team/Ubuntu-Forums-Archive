---
title: "Error Code (1)"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by pr1me on 2010-01-15
Hi ppl,

Lets start with the fact I'm a complete newb when it comes to linux.

Now to the reason for my post: I've been trying various distro's of linux and got stuck with Karmic on 1 machine and Mint Helena on the other - they seemed pretty straightforward until I tried to install a package on both machines which was not in the repository and got this error:

E: The package ... needs to be reinstalled, but I can't find an archive for it. Error Code (1). Please report.

Once again on both machines.

Now, I've searched countless forums for the better part of 2 days to resolve the issue as it wouldn't let me update, install packages, remove packages ... to no avail, until I found these instruction a few minutes ago:

"Corrupt Package Problem: Resolved

E: The package ... needs to be reinstalled, but I can't find an archive for it. Error Code (1). Please report.

sudo gedit /var/lib/dpkg/status

Search through the file for any reference to [package/program name] and CAREFULLY delete that entry.

Save the file

Then use code:

sudo apt-get update

Your problem should now be solved"

For other newbies out there who might be having the same problems, this is the way to go on both Ubuntu 9.10 Karmic Koala and Mint 8 Helena (funny that ;))


Good luck and good day,
Yours truly,
pr1me

---

### Post by cariboo on 2010-01-17
Not so funny really as Mint is based on Ubuntu, and Ubuntu is based on Debian.

---

