---
title: "Can't start Thunderbird in one user account"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by jotiho on 2009-09-07
I have set up a new xubuntu system with three user accounts. On one of these accounts Thunderbird refuses to start, and gives the error message "Thunderbird is already running. To open a new window, you must first close the existing Thunderbird process, or re-start your system."

I have tried
* re-booting, 
* un-installing and re-installing Thunderbird, 
* comparing the process list (ps -efH) in the problem user account with that in an account which _will_ run Tbird  and killing any process that didn't have a direct analogue in the good account. (There was only one, with CMD=  "/usr/bin/Thunar --daemon" , and killing this made no difference.)

None of these has fixed the problem. 

I'm now at a loss. It looks as though Tbird really isn't running, but the system thinks it is, and I need to find and fix the setting which gives the appearance of Tbird being active.

I'd be very grateful for any suggestions...

---

### Post by yeats on 2009-09-07
This might help:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by jotiho on 2009-09-07
thanks. Resource looks useful, and points to a lock file problem as likely cause. But deleting .parentlock  file did not fix it. There was no lock file - does this suggest anything? I'm assuming the lock file(s) appear in the xxxxxxxx.default  folder?

---

### Post by yeats on 2009-09-07
What happens when you delete the .default profile folder in the affected user profile?  It may fix itself.

---

### Post by jotiho on 2009-09-07
Yup, that fixed it! Many thanks.

Now I've got another (smaller) problem - how do I re-assemble the emails I've now got split over three separate profiles (I'd already been experimenting over the last few days with creating new profiles to solve   the problem).   Can you, for example, just concatenate mailbox files (eg <default folder>/Mail/Local Folders/Inbox)?

---

### Post by yeats on 2009-09-07
> Now I've got another (smaller) problem - how do I re-assemble the emails I've now got split over three separate profiles (I'd already been experimenting over the last few days with creating new profiles to solve the problem). Can you, for example, just concatenate mailbox files (eg <default folder>/Mail/Local Folders/Inbox)?

This I don't know... I would imagine a search through Mozilla's knowledge base would help at least know in which folder the emails are kept.

---

### Post by jotiho on 2009-09-08
Thanks.  Looks like I need the export/import add-in.

From my experience so far I'd say the profile management functionality in Tbird could do with some rethinking. But at least my original problem is resolved (if not solved in the sense of understanding what had gone wrong).

Thanks for your help, and best regards.

---

### Post by yeats on 2009-09-08
> From my experience so far I'd say the profile management functionality in Tbird could do with some rethinking. But at least my original problem is resolved (if not solved in the sense of understanding what had gone wrong).

You *should* be able to add a "-profilemanager" flag to the command that invokes Thunderbird (after the "application.ini" part), and that would let you create alternative profiles.  This is built-in Mozilla/XUL functionality and would also work for Firefox, Songbird, etc. (in theory - I haven't tried them all).

---

