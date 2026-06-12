---
title: "reinstall question on users"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by eddski on 2009-09-04
If I do a reinstall, without formatting my /home partition, will I have a problem with security id's or ownership on the new system with the users that were on the old /home partition?

---

### Post by tomBorgia on 2009-09-04
I've never had any problems... If you recreate the username the same it should be ok.

---

### Post by 3rdalbum on 2009-09-04
When you install the new system, you'll be asked if you want to migrate the old user accounts over - just don't elect to format the disk! Your /home will still be preserved and user accounts will be as normal.

---

### Post by perce on 2009-09-04
As far as I know, the first user you create has always user id 1000. Since your user id before and after reformatting will be the same, you will have no problems. 

If you have multiple users, I have no idea what happens but I'm sure you can change a user's user id even after creating it, so you can easily fix any problem you may have.

It's the user id that matters for permissions, not the user name.

---

