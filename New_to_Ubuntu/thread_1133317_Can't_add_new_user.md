---
title: "Can't add new user"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by freakky on 2009-04-22
I can't seem to be able to add a new user.  I go to System/Administration/Users and Groups.  But the Add User button is grey (can't click on it).

The only users I see are the original user I created when I installed Ubuntu, and root (root is grey as well - can't choose it; which I think Ubuntu doesn't allow).

I installed Ubuntu 8.10 a couple of days ago.  I'm able to install applications with the one user account I have; so I'm thoroughly confused.

Please let me know if any additional information would be helpful.
This is my first attempt to use linux and thus Ubuntu.  Any help or suggestions would be greatly appreciated.

---

### Post by mikewhatever on 2009-04-22
What about the unlock button below? You have to unlock the interface by entering your password first.

---

### Post by llamabr on 2009-04-22
You can always also use the command

```
sudo useradd username
```

from the terminal

---

### Post by egalvan on 2009-04-22
> **mikewhatever said:**
> What about the u**nlock button **below? You have to unlock the interface by entering your password first.


+1

This totally threw me the first two or three times I used these functions.
I thought my Ubuntu was broken. :)

Check it out carefully.

click on the "unlock" button:

---

### Post by egalvan on 2009-04-22
> **llamabr said:**
> You can always also use the command

```
sudo useradd username
```

from the terminal

yep, this is easier. No silly "unlock" button to remember.

It's why I love the command line. :)

---

### Post by freakky on 2009-04-24
Thanks for the help.  That worked perfectly.
The screen shot was a nice touch egalvan.

I guess I'll stumble more than I anticipated when trying to execute  'easy' stuff; learning a new operating system takes some time.

Thanks for the help.

---

