---
title: "Adding A User account?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Ira_S on 2010-01-17
Whenever i go to the User account editor,  the button for adding a user is disabled.


how can i do it with the command?


PS:  Useradd NAME doesent work,

---

### Post by kenuf on 2010-01-17
When I go to
System> Administration> Users and Groups
Near the bottom of that little window is a button with a little keyring on it...
When I click that it asks for the password.
Then it makes the fields available.

---

### Post by admiralspark on 2010-01-17
in the bottom center of the screen that pops up, there is a button with keys on it. Click on it to unlock the options (I believe it has to be run as root through that, good security practice).

---

### Post by Jive Turkey on 2010-01-17
try this:```
sudo adduser <username>
```

---

### Post by Ira_S on 2010-01-17
wow who could of thought that it would be so simple,  thats a dum feature lol......  Linux needs to make Ubuntu more user freindly

---

### Post by baddog144 on 2010-01-17
> **Ira_S said:**
> Whenever i go to the User account editor,  the button for adding a user is disabled.


how can i do it with the command?


PS:  Useradd NAME doesent work,

Did you make sure 'useradd' was all lowercase, and that you were running as root (`sudo useradd NAME`)?

---

### Post by admiralspark on 2010-01-17
Why couldn't you just use the GUI and unlock it by clicking on the set of keys? That seems alot easier than using the command line.....

---

### Post by JackRock on 2010-01-17
> **admiralspark said:**
> Why couldn't you just use the GUI and unlock it by clicking on the set of keys? That seems alot easier than using the command line.....

This doesn't always work.  I myself have been trying to do that, and clicking on the keyring doesn't do a thing.  It doesn't ask for the password or anything at all.

---

### Post by 3rdalbum on 2010-01-17
> **Ira_S said:**
> wow who could of thought that it would be so simple,  thats a dum feature lol......  Linux needs to make Ubuntu more user freindly

1. I've never heard complaints about this before, not even from Mac OS X users who have had a similar feature since 2000

2. It's part of the security system, that allows system administrators to grant specific privileges to individual users without giving them 'sudo' access or the root password, both of which place too much power in a user's hands.

3. Linux is not a company, it's a piece of software.

---

