---
title: "ubuntu ROOT user $HOME"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-05-18
hey i recently did an overhaul of my laptop and installed windows 7 RC and ubuntu (9.04) things were fine at first i was able to download updates and other stuff for ubuntu but recently i have been getting an error message at startup 

"User's $HOME /.drmc file is being ignored ....File should be owned by the user and have 644 permission. User's $HOME directory must be owned by user and not writable by other users." 

and when i try to update archive manager by typing apt -get install unrar i get this message 

E: unable to open lock file /var/lib/dpkg/lock - open (13 permission denied) 
E: unable to lock the administration directory (/var/lib/dpkg/), are you root? 

thats all the info i have at the moment and im hoping someone can help me.
Thanks in advance

---

### Post by The Cog on 2009-05-18
You could try deleting .dmrc (it will be recreated as needed):
**sudo rm ~/.dmrc**

You need sudo for apt-get too - like this:
**sudo apt -get install unrar**

---

### Post by Bölvaður on 2009-05-18
> **The Cog said:**
> You could try deleting .dmrc (it will be recreated as needed):
**sudo rm ~/.dmrc**


if you open the terminal "Applications &#8594; Accessories &#8594; Terminal" that is supposed to be
```
rm .dmrc
```

---

### Post by pendulum101 on 2009-05-18
> **Bölvaður said:**
> if you open the terminal "Applications &#8594; Accessories &#8594; Terminal" that is supposed to be
```
rm .dmrc
```

i tried to remove the file using the given terminal commands and i restarted the computer but im am still getting the same warning as before. when i tried to delete the file using rm .dmrc it said that the file didnt exist
any ideas?

---

### Post by coffeecat on 2009-05-18
If you look at the original error you'll see that it was complaining about permissions on .dmrc and/or $HOME. If you're still getting the error, try this. Open a terminal, and:

```
chmod 700 ~
```

---

### Post by bayvista on 2009-06-09
Thanks for that. The "chmod 700 ~" seems to have fixed my problem.

---

### Post by steve-o1983 on 2009-06-28
I had the same error after trying to share some files between users.  I was able to fix the problem by changing the permissions of the .drmc file itself so that the GROUP and OTHER access was NONE.  Worked well for me, just in case it ever happens again.:guitar:

---

