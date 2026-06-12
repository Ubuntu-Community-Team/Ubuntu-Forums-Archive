---
title: "Elevate new account so I can delete my current one"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by silverfang77 on 2009-09-09
I've decided to give my Ubuntu laptop to my friend. I've already created a user account for her. Now I wish to delete mine. The problem is I can't delete mine while I'm logged into it and when I try to do it from hers using the sudo command, it says the account isn't a "sudoer" and that the attempt is being reported, which indicates to me that the new account doesn't have privileges to use sudo.

So my question is, how do I elevate the new account so I can delete the old one?

A Google search of elevate account ubuntu yielded nothing.

Thank you.

---

### Post by Hospadar on 2009-09-09
You need to add her to the group "admin" - this will allow her to use sudo, I think you add groups in the same place you add and delete users, or you can use the command line - look it up on google.

After that she'll be able to sudo and you can delete your old user account - you'll probably have to delete you home folder separately.

You may need to restart after adding her to the group, but I don't think so.

---

### Post by silverfang77 on 2009-09-09
I assume you mean Users and Groups under System>Administration. I'm in her user account properties, but the entire permissions tab is grayed out and inaccessible for me.

edit: I tried adding her to the admin group using the terminal command sudo users-admin friendsname, but received an error message: (users-admin:5111): CRITICAL **: Unable to lookup session information for process '5111'

What does that mean?

---

