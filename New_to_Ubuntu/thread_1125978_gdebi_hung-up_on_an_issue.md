---
title: "gdebi hung-up on an issue"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by lotusalive on 2009-04-14
I wanted to use gdebi to install RealPlayer11GOLD for linux tonight, it would not install the dependencies or the download, BECAUSE of mxallowd not being completely installed...  I can't utilize gdebi to install anything because of this problem...

So, I went to use the command line to attempt to uninstall it again, results:

sol@sol-desktop:~$ root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
bash: root@sol-desktop:/home/sol#: No such file or directory
sol@sol-desktop:~$ su
Password:
root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@sol-desktop:/home/sol#

No other process is open on my desktop, and I don't know why this is, or what it means...

---

### Post by jbrown96 on 2009-04-14
> **lotusalive said:**
> I wanted to use gdebi to install RealPlayer11GOLD for linux tonight, it would not install the dependencies or the download, BECAUSE of mxallowd not being completely installed...  I can't utilize gdebi to install anything because of this problem...

So, I went to use the command line to attempt to uninstall it again, results:

sol@sol-desktop:~$ root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
bash: root@sol-desktop:/home/sol#: No such file or directory
sol@sol-desktop:~$ su
Password:
root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@sol-desktop:/home/sol#

No other process is open on my desktop, and I don't know why this is, or what it means...

```
sudo rm /var/lib/apt/lists/lock
```

---

### Post by lotusalive on 2009-04-15
Thanks jbrown96, but this is what I get from that command...

sol@sol-desktop:~$ sudo rm /var/lib/apt/lists/lock
[sudo] password for sol: 
sol@sol-desktop:~$ sudo rm /var/lib/apt/lists/lock
rm: cannot remove `/var/lib/apt/lists/lock': No such file or directory
sol@sol-desktop:~$

---

### Post by jbrown96 on 2009-04-15
Try [these]("http://www.webmaster-forums.net/server-management/could-not-get-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error-d") instructions. There's a few different commmands that you can try. Have you tried rebooting? That removes the lock a lot of time.

---

### Post by lotusalive on 2009-04-15
Thank you so much jbrown96 !  I will try that when I have a moment...  Buried for the week, or more...  I hope to let you know.

---

### Post by lotusalive on 2009-05-06
Firestarter started crashing, which is always my indicator that my system has been breached in some way.  Had to reinstall, since I guess I did something further wrong, by uninstalling DHCP, since it had no dependencies, and I am not on a 'network.'  (Home PC)  But that seemed to have caused my PC to be removed from internet access !  o' well.

Now that I've reinstalled, I'd like to back it up, for once.  Will probably have questions...  Thx all.   (Also, can't get any dvd's to play at all, not my own, not netflix rentals ? They really hate us, ? lol...)

:popcorn:

---

