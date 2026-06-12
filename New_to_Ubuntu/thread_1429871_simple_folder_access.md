---
title: "simple folder access ?"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by stonebergftw on 2010-03-14
I know this is simple.

I have 2 users in the home folder, say tim and pete

tim is the admin and is in the sudoers file, pete is not.

Inside /home/tim/ there are a bunch of folders, which tim does **not** want pete to be able to read or write to.

However, tim **does** want everyone else to be able to read from those folders.  He just wants to prevent pete from viewing them.

What is the command to accomplish this?

---

### Post by HereInOz on 2010-03-14
Put Tim and everyone else (except Pete) into a particular Group.  Put Pete into a different Group, but not into the one Tim is in.

Give Tim's group full access to these folders, and give Others (which takes in Pete's group), no access to these folders.

---

### Post by stonebergftw on 2010-03-14
This approach unfortunately won't work for me.

My issue is that I run a ushare client to share the folder /home/tim/Videos to my xbox360.  Since I can't add the xbox as a "user" to any group, I need to specifically block each other group or user.

Any ideas?

---

### Post by J V on 2010-03-14
What you are looking for is an access control list, this will let you give rwx permissions to a specific person... sadly, hardly anyone has needed these so far, and they are "new" in linux, so idk where to find a guide on them, google it I guess :)

---

### Post by stonebergftw on 2010-03-14
acl is exactly what I'm looking for.  Thanks a ton.

---

