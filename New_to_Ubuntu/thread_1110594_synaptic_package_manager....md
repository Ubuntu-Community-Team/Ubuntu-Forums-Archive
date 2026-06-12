---
title: "synaptic package manager..."
date: 2009-03-29
forum: New to Ubuntu
---

### Post by nolte on 2009-03-29
ok so i did an update once i installed ubuntu and now i cant lunch any admin programs i was wondering how to fix this. 
 thanx:confused:




:duel boot mac and ubuntu

---

### Post by Sarai the Geek on 2009-03-29
Can you describe the problem a little more? What happens when you try to run synaptic?

---

### Post by oOarthurOo on 2009-03-29
Ubuntu allows certain groups to do things, like use cd drives, listen to audio, and use admin programs. If your user suddenly can't do something you should check to ensure your user belongs to the groups that let them do that.

For things like admin programs you need to make sure your user is a member of the 'admin' group.

In a terminal, when logged on as your user, type "groups" and hit enter. You'll see which groups you belong to. If you don't see admin then I think we've found the problem.

If not, then you should try running the program from the terminal, because that will give you more detailed error messages about what the problem might be.

---

