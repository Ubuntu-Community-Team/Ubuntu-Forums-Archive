---
title: "Resurecting an old user"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by brawd on 2010-02-04
Hi,

I need to add back an old user account that had been deleted.
When I use Admin/Users/Newuser to input the details, the user name, real name etc... It comes back with the message user already exists.
The problem being We can't access the account. It's not displayed at the log on screen. From Terminal I can go to the directory and list the files there.
Anyone know how to re-activate this account please?

regards

brawd

---

### Post by anaconda on 2010-02-04
hmm.. 
I dont know if this will work, but 

I would first backup the home folder of that user, and then delete his home folder
And then I would try to add him as a new user with
```
sudo adduser username
```

And then finally you can copy his files back to his new home-folder..

And why? When you doelete a user his home directory wont be deleted by default, but If I remember correctly he is removed from everywhere else.

And I GUESS the fact that the home-folder still exists prevents a new user with the same name from being created.. 

PS.it might be a good idea to create the new user with the same UID and GID (User id and groupID) than what they used to be.  
Man adduser will tell you how to do this...

---

### Post by ibuclaw on 2010-02-04
How did you deactivate/delete it?

Does:
```
grep "**username**" /etc/passwd
```
Output anything? (replace 'username' with the user's real username).

Secondly, does their home directory exist?

Regards
Iain

---

### Post by brawd on 2010-02-04
Thank you, all done.

It restored everything and is available on logon page.

Incidently it was deleted because I couldn't change the pwd by the regular means. The deleting of the account was merely a flash of (not very bright) brilliance.

To finish 'grep' came back with nothing and 'adduser' did the trick.

thanks again


brawd

---

