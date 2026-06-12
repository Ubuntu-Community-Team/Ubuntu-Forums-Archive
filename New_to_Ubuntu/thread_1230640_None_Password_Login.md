---
title: "None Password Login?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by jacklinux on 2009-08-03
is it possble to set a log in with none-admin prevelages for my family to use without having to log in. And could i set this as the default logon however i am able to log into the admin (root) user so i can change hardware/software.
Thanks.

---

### Post by TeoBigusGeekus on 2009-08-03
System-> Administration-> Login Window
Go to Security Tab.

---

### Post by jacklinux on 2009-08-03
> **TeoBigusGeekus said:**
> System-> Administration-> Login Window
Go to Security Tab.
Thanks. Now how would i log onto the admin from the default user?

---

### Post by TeoBigusGeekus on 2009-08-03
You don't have to log on to a different account. Whenever you try to change something crucial in the system, Ubuntu asks for the administrator password. Give it and make any changes you want.
Just make sure you won't reveal it to your family...:P

---

### Post by mprince on 2009-08-03
What TeoBigusGeekus suggests will probably meet your needs, but if you want to keep your files separate from theirs then you could setup a new user account that is different for your family and has less privileges.

Just go to *System->Administration->Users and Groups* Unlock using the unlock button-- then click the +Add User button. 

The User Privileges tab will let you choose what they can and cannot do. Be sure the box that says "Administer Account" is unchecked for their account.

The new account would have it's own password and it's own folder under /home so their files and yours would be kept separate. You could switch back and forth by going to switch user on the logout screen... or use the fast user switching which is probably up next to the calendar.

You may want to set their account to be the one that logs in automatically under:
System-> Administration-> Login Window->Security Tab

---

### Post by NoonienSoong97 on 2009-08-06
One question I have noticed that the password window doesn't pop-up when you do certain things. For example, I am trying to change or disable the time on the duel boot screen, and I can't just place fonts in the fonts folder without admin. access. In both of these situations the password window doesn't pop-up.

I have also tried to log in as admin from the log-in screen but ubuntu won't allow it.

---

