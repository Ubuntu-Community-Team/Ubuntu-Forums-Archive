---
title: "Update Manager Protocol &amp; A Question on a Warning"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Brother_Marquis on 2009-04-11
Hi Folks,
I'm a Ubuntu n00b but have decided to break away from my MS dependency and use it on my school laptop.  It's been running great and when I see update manager notifications, I accept them without question.  First, should I be doing this?  I stayed away from Window's update manager because it was like the plague but assumed Ubuntu/Linux would be OK.  Is this smart thinking?

Today, I accepted the latest update but after supplying my admin password, I got a warning that read

[INDENT]"Warning  You are about to install software that **can't be authenticated**!  Doing this could allow a malicious individual to damage or take control of your system"[/INDENT]

Thanks for the help,
George

---

### Post by waspbr on 2009-04-11
sure, though it is optional. You don't have to update but it is nice to have the newest programs with the newest features. The default settings only download the stable update so I would say you are pretty safe.

---

### Post by Brother_Marquis on 2009-04-11
Thanks for the quick reply.  So I can ignore that warning?

---

### Post by Pappy2003 on 2009-04-11
If you want to be safe only download from the Canonical repos.

---

### Post by clive littlewood on 2009-04-11
Hi

That warning is usually associated with third party updates and is saying that because Ubuntu (Canonical) do not maintain that file they must warn you.

However all packages are very carefully checked before being allowed into the repos.

So don't worry and carry on updating.     :p

Clive

---

### Post by ubudog on 2009-04-11
Thanks I was about to ask the same question!

---

### Post by 3rdalbum on 2009-04-11
If you know what repository you are using that has caused this warning, you could find out from the maintainer what the GPG key is, and then add it to your Apt system. That will end the warnings as the packages will be authenticated.

Personally I don't tend to bother, although I should as it guarantees that the package has not been tampered with in transit.

The updates are perfectly safe; I even use the Proposed updates without a problem (although you shouldn't unless you don't mind breakage!).

---

