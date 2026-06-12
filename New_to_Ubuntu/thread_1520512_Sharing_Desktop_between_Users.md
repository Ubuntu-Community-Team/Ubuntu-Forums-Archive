---
title: "Sharing Desktop between Users"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by saltwater43 on 2010-06-29
I loaded Ubuntu 9.10 for my kids, and I used my login and desktop.  I now want to be able to do two different things.

1) I want to form another account (which I did), but I don't know how to load all of the desktop games and such from my account to theirs.  I've used the cp command from the terminal server and finally successfully copied "Chess" from my account to theirs, except theirs come up with a little Lock on the upper right corner of the Chess App on the desktop. I used cp /home/user/Desktop/chess /home/Kids/desktop, I think.  There has to be and easier way.

2) I would like to have a backup file in case they mess up their desktop so I can just reload the desktop apps.  There will be no internet connection. What permissions should I give their account so they can run the apps but not cause too much trouble with the rest of the system?  Again, I would clean it up from a terminal server, I hope.

Thanks,
Chuck

---

### Post by -humanaut- on 2010-06-29
What command did you use to add the users? I believe useradd will give them permissions to access games,etc. adduser you have to set permissions manually. I recommend if you use useradd remove them from root.

---

### Post by saltwater43 on 2010-06-29
In "Linux for Dummies", it didn't mention a User Add command.  I didn't find it searching the Forums either, because I didn't know what exactly to search for.  I will try it.  I really appreciate your reply. It'll be tomorrow 'till I know the results.

Thanks,
Chuck

---

### Post by saltwater43 on 2010-06-30
What about the second part.  How would I save all of the desktop to a directory to be reinstalled at the desktop at a later date when they messed this one up?
Thanks for you patience.
 
Chuck

---

### Post by saltwater43 on 2010-07-02
I figured it out. I copied the desktop Apps to another folder, which seems basic, but I'm just learning. 
Thanks for helping.
Chuck

---

