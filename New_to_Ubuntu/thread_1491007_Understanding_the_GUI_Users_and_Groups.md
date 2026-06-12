---
title: "Understanding the GUI Users and Groups"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by holocene on 2010-05-23
Greetings

My question is what is the relationship to the GUI Users and Groups view of group membership? I don't see any user in the group that I expect.

For instance. When I view the ownership and primary group of a directory I get:

holocene@crypt:~$ ls -l | grep permissions
drwxr-x--- 2 holocene holocene    4096 2010-05-23 00:30 permissions

Which I believe is a directory called "permissions" which is owned by holocene whose primary group is holocene.

However, when I select System|Administration|Users and Groups and select the user holocene, click on manage groups, then scroll down and select the group holocene, then properties, there are three users listed, however there are no checked boxes. 

What am I missing?

Regards
Steve.

---

### Post by holocene on 2010-05-23
Someone advised that the graphical dialog "Users and Groups" does not show user's membership in the Private Group. 

This was confusing to me and maybe others. It would be nice to have it documented, or fixed.

Best Regards
Steve.

---

