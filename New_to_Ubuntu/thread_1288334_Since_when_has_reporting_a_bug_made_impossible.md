---
title: "Since when has reporting a bug made impossible?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by uflieven on 2009-10-11
I want to report a bug about grub2. The problem is, after doing a command-line install of Kubuntu-9.10-beta-alternate-i386.iso, there are no grub entries for other operating systems, like Windows XP, or other linux versions.

But the real problem is, I can't file the bug report. This needs some explanation.

I always start from [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs). Under When not to file a bug - Already filed, there's a link to go to the existing bugs. When followed, it directs me to [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs). In the upper right top of the page there's a button Report a bug. When clicked, it directs me to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs). As you see, this is the page I came from. So right now I'm running in circles.

Anyone, please help...

---

### Post by ibuclaw on 2009-10-11
Hi, please see our [Grub2 Introduction Thread]("http://ubuntuforums.org/showthread.php?t=1285897").

And try running:
```
sudo upate-grub
```
And reboot to see if that resolves your issue.

Regards
Iain

---

### Post by diesch on 2009-10-11
The prefered way to report a bug is to use [ubuntu-bug](https://help.ubuntu.com/community/ReportingBugs#Filing%20a%20bug%20with%20ubuntu-bug), but you can still use [Launchpad]("https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net") if you want.

---

### Post by uflieven on 2009-10-11
Thanks, tinivole, that solved it. But then i'm still wondering, why the debian-installer doesn't run sudo update-grub. I mean, with grub it wasn't necessary to manually run sudo update-grub, but with grub2 it is. Why?

Secondly, reporting a bug still seems impossible. Ok, I don't really need it any more right now, but it should be fixed as soon as possible.

---

### Post by philinux on 2009-10-11
> **uflieven said:**
> Thanks, tinivole, that solved it. But then i'm still wondering, why the debian-installer doesn't run sudo update-grub. I mean, with grub it wasn't necessary to manually run sudo update-grub, but with grub2 it is. Why?

Secondly, reporting a bug still seems impossible. Ok, I don't really need it any more right now, but it should be fixed as soon as possible.

ubuntu-bug is the best way as it collects system info, but if you dont know the package then go here.
[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)
then this link
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

---

### Post by slakkie on 2009-10-11
Add a comment here [https://bugs.launchpad.net/bugs/432324](https://bugs.launchpad.net/bugs/432324) if you want the report a bug button to work again (propperly). And subscribe yourself to the bug.

You are not the only one who is annoyed by the current behavior.

---

### Post by uflieven on 2009-10-11
Thanks philinux, your second link actually makes it possible to report a bug (at first sight). I will keep this page handy in case I have to report a bug in the future.

@slakkie: If others also have problems with it, the chance is bigger it gets fixed, so I hope it will be in the next days.

Thanks for all the help, I consider this as solved.

---

