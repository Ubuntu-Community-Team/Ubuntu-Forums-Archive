---
title: "disable system updates"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-22
How do I completely disable system updates for an account with limited privileges? It keeps telling me I need to enter the password, then tells me I'm not allowed (obviously).  If I log in as root, how can I control the settings for the limited account?

---

### Post by ptn107 on 2009-12-22
Limited accounts cannot update the system.

---

### Post by cartisdm on 2009-12-22
> **ptn107 said:**
> Limited accounts cannot update the system.

I'm putting this system together for my grandmother down in Alabama so I want to make sure it's completely no maintenance for her.  So with a limited account she won't be bothered by any popups to update her system or anything similar to that I might be overlooking?

---

### Post by 3rdalbum on 2009-12-22
In the user's System > Preferences > Startup Applications, disable "update-notifier".

You might also want to use "Install Security Updates Automatically" and "Check for Updates Daily" in System > Administration > Software Sources, so your grandma always has the latest security fixes. There's pretty much no risk in installing security updates (or, less risk than running an unpatched system).

---

### Post by cartisdm on 2009-12-22
> **3rdalbum said:**
> In the user's System > Preferences > Startup Applications, disable "update-notifier".

You might also want to use "Install Security Updates Automatically" and "Check for Updates Daily" in System > Administration > Software Sources, so your grandma always has the latest security fixes. There's pretty much no risk in installing security updates (or, less risk than running an unpatched system).

Cool thanks for the advice.  Also, to save from starting a new thread:

How can I make sure I have everything set up like I need for Remote Desktop? She will be connected directly through the modem via wired connection so I won't have to worry about a router.  I will NOT be the one hooking up the computer down in Alabama so I want to make sure I can everything I need to be able to Remote Connect from my house in Virginia.

---

### Post by 3rdalbum on 2009-12-22
System > Preferences > Remote Desktop.

click "Allow other users to view your desktop" and "Allow other users to control your desktop". Under security choose one of the first two options, and click the third box ("Configure network automatically").

---

