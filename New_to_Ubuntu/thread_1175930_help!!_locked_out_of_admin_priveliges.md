---
title: "help!! locked out of admin priveliges"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by fenix1982 on 2009-06-01
My friend lent my webook, it has ubuntu version 8.01 i think it is....anyway long story short she's deleted the  admin user account, and now im locked out of making changes, ive tried adding user but once you log in as her it's all single user and locked cant even use the root terminal because that needs admin password but there is no admin user.

im used to windows myself, so if anyone can shed some light on this i would be gratefull, i have no idea on this system and am stumped lol

---

### Post by Didius Falco on 2009-06-01
> **fenix1982 said:**
> My friend lent my webook, it has ubuntu version 8.01 i think it is....anyway long story short she's deleted the  admin user account, and now im locked out of making changes, ive tried adding user but once you log in as her it's all single user and locked cant even use the root terminal because that needs admin password but there is no admin user.

im used to windows myself, so if anyone can shed some light on this i would be gratefull, i have no idea on this system and am stumped lol

Hi,

Boot up into Recovery Mode. Choose the Root Shell or Net Root option when you reach the menu. This will boot into a black screen with a command line, with Root powers.

type ```
adduser username admin

``` to create a new user account with admin powers. Then set the password by typing ```
passwd  username
``` you'll be prompted to type the new password. It doe not show any visual signs (no **** as you type, for example) but it is recording the password. You'll then have to type it a second time.

Then you can type ```
reboot now 
``` and you should be able to log in normally, under the account you added above.

Regards,

Didius

---

### Post by fenix1982 on 2009-06-01
thanks for that it's worked a treat, but 1 small problem, ive had to give another username for admin privaliges the original user it tells me cant be logged into from the log on screen where else would i go ??, it still shows in users as root though? im confused lol

---

### Post by Didius Falco on 2009-06-01
Now that you have an account with Admin privileges, you can use that account to reset the other account. Logged in under the account with Admin privileges, go to S**ystem/Administration/Users and Groups** and open that up. You'll have to unlock it with your password, and then you can set up a new user, change the privileges on other users, etc.

Regards,

Didius

---

### Post by Iowan on 2009-06-01
Another option is to check /etc/passwd to see what shell the old admin is set to use - /bin/false means no login.  Check the link in my sig for psychocats - there are several useful topics there for sudo and passwords.

---

### Post by Yehudah on 2009-06-03
I had the same problem and "fixed" it by readding my account to the admin group.

I can do sudo, but I still am not allowed to do anything.  The error message says that I have to be a superuser to do this function.

This is a new dual boot install, one day old.  I'm trying to install the ATI drivers in a terminal window.

...getting very frustrated.

Any hints?

---

### Post by Didius Falco on 2009-06-04
> **Yehudah said:**
> I had the same problem and "fixed" it by readding my account to the admin group.

I can do sudo, but I still am not allowed to do anything.  The error message says that I have to be a superuser to do this function.

This is a new dual boot install, one day old.  I'm trying to install the ATI drivers in a terminal window.

...getting very frustrated.

Any hints?

Hi,

You should really start your own thread for questions. That way more people will see it - I almost didn't open this, because the name on the last post was different than the name that started the thread.

Can you tell us what, exactly, the command is you are trying to run, and the exact error message, please.

Also, make sure you don't have Add/Remove or Synaptic open when you are trying to run this command - that will often throw up an error when you are trying to install something from the command line.

Regards,

Didius

---

### Post by Yehudah on 2009-06-04
I love the search function.... sorry to post too soon. 

I went into recovery mode and re-added my username to the admin group, that helped.  Once in a term windows, I still couldn't load the drivers, said I didn't have permission.  I did a sudo -s and it worked.

I'm okay with that.  It worked.  I appreciate your response.  Next time I'll look harder.

---

