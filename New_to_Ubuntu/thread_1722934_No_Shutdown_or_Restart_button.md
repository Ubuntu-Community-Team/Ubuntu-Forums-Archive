---
title: "No Shutdown or Restart button"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by maembe on 2011-04-06
So I finally got kubuntu working, but I quickly realized that the only "Leave" option is to log out.  There is not shutdown or restart option.  I did sudo apt-get install kshutdown and it gave me this nice little app that has shutdown, restart, logout, etc.  But it doesn't work.  I select shutdown and it just won't do anything.

Anyone have any ideas?

---

### Post by rosencrantz on 2011-04-06
Hi maembe,
you probably don't have the proper permissions. Check the KDE system settings.
a) There should be an entry right at the bottom called 'Login Screen'. Go to the Shutdown tab and make sure the dropdown box under 'Local' reads 'Everybody'. 
b) You can also check the 'Startup and Shutdown' entry in the main menu, in the subentry 'Session Management' the checkboxes 'Confirm logout' and 'Offer shutdown options' should be enabled.

I think point a) is the important one.
If that doesn't work, check the permissions for /sbin/halt and /sbin/reboot from the command line, it should look like this (from my standard Kubuntu 10.10):
```
$ ls -l /sbin/ha*
lrwxrwxrwx 1 root root 6 2011-02-02 12:30 /sbin/halt -> reboot
$ ls -l /sbin/reb*
-rwxr-xr-x 1 root root 9696 2011-01-21 21:01 /sbin/reboot
```
So /sbin/halt just links to /sbin/reboot and everybody has permission to execute /sbin/reboot (note the 3 x's, check out this link on permissions and how to change them [http://www.washington.edu/computing/unix/permissions.html](http://www.washington.edu/computing/unix/permissions.html))
Test executing /sbin/reboot from the command line and see whether it shuts down.
Cheers,
rosencrantz

---

### Post by maembe on 2011-04-06
Okay, so I tried /sbin/reboot and it said 'reboot:  need to be root'
So I did sudo /sbin/reboot and it worked just fine, so I'm guessing it's a permissions issue.  I'm not really sure what to do though.
My permissions are the same as yours.

---

### Post by rosencrantz on 2011-04-06
Erm, I need to be root for that, too, and it seems to be permission independent (check man reboot). Sorry, I didn't want to shutdown earlier and didn't test it.
Considering I can shutdown all right, your permissions should be OK, too.

Did you check the KDE system settings?

---

### Post by maembe on 2011-04-06
> **rosencrantz said:**
> Erm, I need to be root for that, too, and it seems to be permission independent (check man reboot). Sorry, I didn't want to shutdown earlier and didn't test it.
Considering I can shutdown all right, your permissions should be OK, too.

Did you check the KDE system settings?

Yeah, it all checks out.

---

### Post by rosencrantz on 2011-04-06
Curious. Are you a regular user on a standard install? No guest account, wubi or live system?

---

### Post by maembe on 2011-04-06
> **rosencrantz said:**
> Curious. Are you a regular user on a standard install? No guest account, wubi or live system?

Yes, I believe so.  I'm the only user and I'm logged in under my account.  I did a standard install as well.

---

### Post by rosencrantz on 2011-04-06
Um. Any more bright ideas will require major googling.
In the meantime you can always do [FONT="Courier New"]sudo shutdown -r now[/FONT] for reboot and [FONT="Courier New"]sudo shutdown -h now[/FONT] for shutdown, but this is far from ideal.
Another thing you could test would be to create a new user and see whether the problem persists on a different account. In that case, there is something wrong with the configuration in your home directory.

---

### Post by maembe on 2011-04-07
Well, I fixed it, but I'm not sure exactly how.  I had already moved on to working on something else.  In my software settings I checked backports box of Origin of Packages, so maybe that did it.

---

