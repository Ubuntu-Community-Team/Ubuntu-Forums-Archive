---
title: "Uninstalled nautilus and now can't log in session"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by IsolatedSheep on 2010-03-17
Just like what the title says, I uninstalled nautilus and then reinstall it back, but after reboot I can't login to gnome session. How can I fix this? Thanks in advance.

Btw, I'm using Ubuntu 9.10 amd64. Grub is fine, just can't login after gdm. I uninstall nautilus using `apt-get purge nautilus` and reinstall using `apt-get install nautilus`.

---

### Post by lidex on 2010-03-18
So you get to login screen and enter username and password; what happens then?
Any error messages?
Check this post to get relevant log data and post it here:
[http://ubuntuforums.org/showpost.php?p=4939442&postcount=2]("http://ubuntuforums.org/showpost.php?p=4939442&postcount=2")

Just out of curiosity - why would you uninstall nautilus?

---

### Post by IsolatedSheep on 2010-03-21
@lidex, actually this problem is solved. I should marked it as that sorry. :)
Anyway, I installed nautilus-elementary, and I want old nautilus back. So I thought removing the nautilus packet and reinstalling it would do the job. Turns out doing that also remove the gnome-session and ubuntu-desktop packets. Thus, causing the problem T_T

I solve this problem by booting to LiveCD -> connects to the internet -> view /etc/resolv.conf -> Copy IP address -> chroot to Filesystem -> sudo apt-get update && sudo apt-get install ubuntu-desktop -> Reboot and boot to Filesystem -> Problem solved -> Yay! :D

Thanks for replying though ^.~

---

### Post by enobrev on 2010-10-22
I came here for a similar reason, although I hadn't yet gone through with removing nautilus and hence ubuntu-desktop.  If you installed nautilus-elementary via a ppa, you can remove it by purging the ppa:

This did the job for me:
```

> sudo apt-get install ppa-purge
> sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa

```

---

