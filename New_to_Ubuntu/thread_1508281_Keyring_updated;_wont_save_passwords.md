---
title: "Keyring updated; wont save passwords"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-06-12
Hey all

Just the other day, when I updated my system, gnome-keyring was updated.

Ever since then, none of my passwords will 'keep' between sessions. Every time I log in from a reboot, I have to create a new default keyring password, enter my wireless WPA key, my password for gwibber (twitter and facebook) and all of my IM accounts.

What the heck happened that they wont keep, and how do I fix it?

---

### Post by ubunterooster on 2010-06-12
I did> **ubunterooster said:**
>  ```
 rm ~/.gnome2/keyrings 
```  and rebootedwhen had similar problem.

---

### Post by tom.swartz07 on 2010-06-12
> **ubunterooster said:**
> I didwhen had similar problem.

Thanks! 

Ill see how that works out.

---

### Post by tom.swartz07 on 2010-06-13
That didnt work.

Still wont save the keyring. 
I chose to use unsafe storage (i.e. no password) because i dont want to type a darn password twice every time i boot the computer. 

I understand the security risks, etc etc. but i already have a password to log in my user. I dont understand why the keyring (which never gave me a problem until now) is acting so strangely....

---

