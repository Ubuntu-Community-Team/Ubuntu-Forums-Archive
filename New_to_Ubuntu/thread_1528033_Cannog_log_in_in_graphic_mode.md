---
title: "Cannog log in in graphic mode"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by yc2 on 2010-07-10
My own account is set to pass GNOME login screen automatically. That works.

However, other users cannot log in graphically. When I make "change user" in gnome menu and try to log in as other users it seems their passwords are not accepted. (I have some accounts for friends who only do ssh proxy surfing, so they are aware of me knowing and using their passwords.)

My own password is accepted in graphics mode.

Problem is not passwords though. I have reset passwords and can also login in terminal for other users. In terminal I can log into their accounts
```
su username
```
works

Maybe it will still work for my friends when they do SSH, but with important stuff like passwords it is usually best to tie up all loose ends.

I was experimenting with the package libpam-gnome-keyring, but finally removed it. I get the same problem using or removing the package.

Thankful for suggestions how to make other users log into GNOME.

---

### Post by yc2 on 2010-07-10
I apologize for this thread.

I now see that I am starting up the other users in "iron bar shell". I am sure this is what makes graphical log in impossible.

Sorry. :oops:

Thread solved.

---

