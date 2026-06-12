---
title: "how to change username?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by FallFromGrace on 2009-02-12
I am dual-booting Vista and Ubuntu 8.04 on a certified machine, Dell M1330. When I set up Ubuntu I just picked a random username, thinking I could change it once I installed everything. Was I wrong? Is this not possible?

When I go to System -> Administration -> Users and Groups, and try to edit properties, it allows me to edit my "Real Name" but not my Username.

Thoughts?

---

### Post by Hospadar on 2009-02-12
You can change your username, but oftentimes things get a little sticky with permissions and such, the actual name you picked is written into all kinds of files in many places in the system and they might not all get updated correctly.
It often works just fine, but you may encounter problems, so just be warned.
anywho, here's a nice guide:
[http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)
I would just change your name, and not your UID, that would probably cause more problems than a name change.

---

### Post by FallFromGrace on 2009-02-12
I see. So the UID is your login name, and it may cause permission files depending on what I have installed? Are the problems enough that I should know how to uninstall and reinstall Ubuntu before I try it?

Wish I'd known this when I created it =P.

---

### Post by The Cog on 2009-02-12
It might be easiest to just create a new account and begin using that. You can delete the old account once you're happy the new one is working and you have copied all your data across.

---

### Post by bodhi.zazen on 2009-02-12
It is not difficult :

[http://ubuntuforums.org/showpost.php?p=4968235&postcount=3](http://ubuntuforums.org/showpost.php?p=4968235&postcount=3)

If those instructions are too cryptic, let me know and I can explain them.

"new" is the new user name , "old" is the old user name.

---

### Post by noremaku on 2009-04-28
I did this and everything works except, when I try to use the Unlock button on various settings and enter the password it says "Could not authenticate. An unexpected error has occured." That goes for any user, not just the one I modified. Also when I log in as any user, it says "Failed to add entry for user __" Help please!

---

### Post by unutbu on 2009-04-29
What was your old username? If your old username was a substring of 'polkituser' (like 'kit' for example) then I think I see where the trouble lies:
The command ```


sed -i -e 's_kit_new_g' /etc/passwd
```

might have changed 'polkituser' to 'polnewuser'...

---

### Post by noremaku on 2009-04-29
I fixed it. Apparently (and this sounds familiar now) the original user has explicit authorizations that are not carried over with a name change, even if it's the same user. So I changed it back to the original username, using 
sudo usermod -l new(original) old(current)
and set all the authorizations under System>Administration>Authorizations to allow anyone. Then I changed the name back to the one I wanted, and gave explicit authorizations to the user (because you can only give explicit authorizations to usernames that exist).

---

### Post by bodhi.zazen on 2009-04-29
> **noremaku said:**
> I fixed it. Apparently (and this sounds familiar now) the original user has explicit authorizations that are not carried over with a name change, even if it's the same user. So I changed it back to the original username, using 
sudo usermod -l new(original) old(current)
and set all the authorizations under System>Administration>Authorizations to allow anyone. Then I changed the name back to the one I wanted, and gave explicit authorizations to the user (because you can only give explicit authorizations to usernames that exist).

Users are tracked by number not name.

In a terminal enter ```
id
```

So when you create a new user you get a new number.

---

### Post by noremaku on 2009-04-29
> **bodhi.zazen said:**
> Users are tracked by number not name.

In a terminal enter ```
id
```

So when you create a new user you get a new number.

But I didn't create a new user, I changed the name and kept everything else. I know, I thought it wouldn't be an issue because of the number but the explicit authorizations didn't show up when I changed the name.

---

