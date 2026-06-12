---
title: "setting up a user with no rights"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by sm1thson on 2009-12-02
Hi
The way the user and rights work is fine for me (ie asks password before doing anything that changes the system), but i am looking at setting up a laptop with ubuntu on it for my grandparents. I would want them to have no access to anything administrative ever.

How is best to set that up?

---

### Post by pi4r0n on 2009-12-02
1. Go to Administration - > Users and Groups

2. Create new user

3. Go to Preferences and User Privileges tab. Over there you need to un-tick things you _do not_ want them to have access to.

4. In advance tab make sure they (user/s) is set up as **User** in Main group.

---

### Post by marco123 on 2009-12-02
Set up a seperate account for them to use, and don't tell them the Admin password.  Choose "Unprivileged user" when setting up that account.

Set up the computer (ubuntu-restricted-extras and any programs) before you make the account for them and Flash and everything should work fine in their account then.

Marco.

---

### Post by sm1thson on 2009-12-02
ok thanks, that should be straight forward enough. I'll give it a trial run on my wifes laptop (I'm stuck on windows for work) and post back if i hit any questions.

---

