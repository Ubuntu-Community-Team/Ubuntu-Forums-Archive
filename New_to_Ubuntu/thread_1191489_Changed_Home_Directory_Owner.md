---
title: "Changed Home Directory Owner"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-06-19
I accidentally did this to my home directory:
> 
chown username:username /home/


Will this make it so other users won't be able to log in? If so, what command do I use to set it back to normal?

---

### Post by Aearenda on 2009-06-19
Did you do it with sudo, or when logged in as root? If not, it probably didn't work. Having the wrong owner may cause trouble later, depending on the permissions that are set.

The correct owner and group for /home are 'root', and the current settings can be shown by the terminal command ```
ls -ld /home
```The output should look something like this:```
drwxr-xr-x 5 root root 4096 2009-03-27 14:30 /home
```
The important parts are the permissions, and the owner and group.

You can put the owner and group right by```

sudo chown root:root /home
```
If the permission string is wrong, you can fix that by```

sudo chmod 755 /home
```

---

### Post by Sup3r3g0 on 2009-06-19
I did it in the terminal with sudo. 

After doing the two commands, here's what I get:
> 
drwxr-xr-x 7 root root 4096 2009-06-18 21:41 /home

Everything looks the same, except for the 5 and 7. Am I fine?

---

### Post by Aearenda on 2009-06-19
Yes, that should be ok. The 5/7 part is the number of links. My system is probably the odd one there, not yours. 

If you have further trouble, look at the ownership and permission of the users' folders at the next level down, which should all belong to their own user and user's group, with the same permissions string as /home itself.

---

### Post by Sup3r3g0 on 2009-06-19
It worked! Thanks for all your help!

---

### Post by Aearenda on 2009-06-19
No worries!

---

### Post by Paqman on 2009-06-19
> **Aearenda said:**
> 
If the permission string is wrong, you can fix that by```

sudo chmod 755 /home
```

Just one point: this leaves everything in your /home executable. You need the directories to be, but the files generally shouldn't be. You can sort that out with this command:

Folders:
```
find . -type d -exec chmod 755 {} \;
```

Files:
```
find . -type f -exec chmod 644 {} \;
```

---

### Post by Aearenda on 2009-06-19
Ummm - there's no -R (recursive) flag in the chmod command I gave.

---

### Post by Paqman on 2009-06-19
> **Aearenda said:**
> Ummm - there's no -R (recursive) flag in the chmod command I gave.

So there isn't, disregard my last then :)

---

### Post by Aearenda on 2009-06-19
You had me thinking I had kangaroos loose in the top paddock for a moment there :-)

---

