---
title: "How to make adduser take effect with out rebooting?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by ineedacold1 on 2009-10-08
Hello,
Is there a way to have the adduser and deluser take effect without rebooting?

I have a script that I add myself to 'muzak' group to change tags on my music, then i remove myself from the group so that I do not mess the tags up.

I have dr-xrwxr-x permission on the folder and the group is muzak, owner is me

---

### Post by nathanagood@yahoo.com on 2009-10-08
Both adduser and deluser take immediate effect--you do not need to reboot.

Can you describe what you're seeing that would lead you to believe it's not working?

---

### Post by CatKiller on 2009-10-08
> **nathanagood@yahoo.com said:**
> Both adduser and deluser take immediate effect--you do not need to reboot.

That's not entirely true. You need to log out and log back in for changes to groups to take effect.

---

### Post by nathanagood@yahoo.com on 2009-10-08
@CatKiller:

Sorry about that--you are correct.  I wasn't thinking about group modifications.

---

### Post by Cypher on 2009-10-08
Could you do change the user's group and then run "su - <user>" and then continue processing? The "su -" should essentially create a new session for that user, wouldn't that mimic logging out and back in?

---

