---
title: "Making a very unprivileged user?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by tacomodo on 2009-04-09
I added a user through the system > Administration > Users and groups, and picked "unprivileged", but he can still read more or less everything.

How can I add a user that can *only* read/write/execute in his own home directory?

Is there an easy way to do this?

Edit: Oh and while I'm at it - how can I disconnect users already logged in?

---

### Post by Didius Falco on 2009-04-09
> **tacomodo said:**
> I added a user through the system > Administration > Users and groups, and picked "unprivileged", but he can still read more or less everything.

How can I add a user that can *only* read/write/execute in his own home directory?

Is there an easy way to do this?

Edit: Oh and while I'm at it - how can I disconnect users already logged in?

This looks like it may be of help in setting up user access permissions:

[http://ubuntuforums.org/archive/index.php/t-567449.html](http://ubuntuforums.org/archive/index.php/t-567449.html)

And this looks like a solution to disconnecting users that are logged in:

[http://www.cyberciti.biz/faq/linux-logout-user-howto/](http://www.cyberciti.biz/faq/linux-logout-user-howto/)

or this one - sounds like a kinder, gentler way to do it

[http://www.go2linux.org/how-to-kill-users-processes](http://www.go2linux.org/how-to-kill-users-processes)

I run a standalone desktop, and my wife would only look at this PC if it was running the Sims 2, but any user that wouldn't log out on request would be an ex-user PDQ. <G>

---

### Post by kanikilu on 2009-04-09
> **tacomodo said:**
> I added a user through the system > Administration > Users and groups, and picked "unprivileged", but he can still read more or less everything. Is there something in particular you want to keep him from accessing? Maybe we can help you set the permissions...

> How can I add a user that can *only* read/write/execute in his own home directory? Someone correct me if I'm wrong, but I think a lot of the files must be readable and executable just for the system to work. For instance, if /bin isn't readable and executable, the user won't be able to do much (anything?). Now if things are *writable* by all, then that's a problem...

> Edit: Oh and while I'm at it - how can I disconnect users already logged in? ```
sudo pkill -u username
``` Should kill all the processes owned by that user, including their shell, which will log them off...

// Edit - Oops, just saw that the link posted above suggests pkill as well...

---

### Post by ranch hand on 2009-04-09
If you use Intrepid there is the "guest session" option.  Can't do jack except in that folder.

The only problem is that folder is gone when you leave that session so anything that needs saved must be on CD/DVD or a USB device.

You could go through and edit the permissions that you don't want the user to have that they still have under your user setup.

This would need to be thought out as to what you don't want them to access as this is a manual process and you could be at it for days if you don't plan it out.

I just created such a user (goofy).  goofy could read my folders.  Came back to here and went to Places->Home folder->File System->Home right clicked Slade->preferences->permissions->others and selected "none" instead of the default "read".  Went back to goofy to check and that stopped goofy from reading Slades' files.

this can be done on a more mass scale through terminal.

---

### Post by tacomodo on 2009-04-09
Hmm it seems this is not as easy as I thought.

After a fair bit of reading it seems what I am looking for is something people call "chroot jail" or something.

Basically I just don't want people logged on to see other mounted disks, system settings, other users home dirs and so forth.

---

### Post by fabricator4 on 2009-04-09
> **tacomodo said:**
> Hmm it seems this is not as easy as I thought.




Maybe not, just remove the 'other' xrw permissions on the top folder of anything you don't what them to see. eg:

```

chmode o-xrw /home/user1

```

and so on.  This will remove all access to user1's home directory for everyone except the owner and the group members.  You can then control selective access to restricted users by giving them limited group access if required.

As someone said, there's some things a restricted user has to be able read, but outside their home dircectory most things will be read only anyway.

There's another forum here called security discussions.  You might read or search those discussions to get some other ideas.

Chris.

---

### Post by juancarlospaco on 2009-04-09
***Guest** Account...*

---

