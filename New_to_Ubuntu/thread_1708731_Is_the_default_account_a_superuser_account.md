---
title: "Is the default account a superuser account?"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by totalanonymity on 2011-03-17
If I'm using the default account made, is it a superuser account? I see things around the internet saying, "Are you root? Don't perform daily tasks as a superuser, unless necessary, etc." Yet, to perform root tasks, don't I need to enter "sudo" every time? Wouldn't that mean I'm not root, unless for the time being when entering that command?

---

### Post by ikt on 2011-03-17
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **totalanonymity said:**
> Wouldn't that mean I'm not root, unless for the time being when entering that command?

For a temporary time after using sudo you have elevated priviliges in some areas of the system.

---

### Post by fabricator4 on 2011-03-17
> **totalanonymity said:**
> If I'm using the default account made, is it a superuser account? I see things around the internet saying, "Are you root? Don't perform daily tasks as a superuser, unless necessary, etc." Yet, to perform root tasks, don't I need to enter "sudo" every time? Wouldn't that mean I'm not root, unless for the time being when entering that command?

Absolutely correct, you are not root.

The default account is an "administrator" account with some customised privileges, which is why when you look at it in users it shows up as type 'custom'.  This account can have root access through the use of 'sudo'. 

It's the best compromise between security and being able to make changes to the system when you really have to.

If you're worried about it, you can make a separate user account with type 'desktop' which can't make any changes to the system at all, however then you can run into problems if you want to update the system or install programs.

Chris.

---

### Post by totalanonymity on 2011-03-17
Thanks. I realized moments after posting that such a general question really should have been researched first. But, can't delete a thread (as far as I know). 

But, thank you. 
:)

---

### Post by ikt on 2011-03-17
> **totalanonymity said:**
> Thanks. I realized moments after posting that such a general question really should have been researched first. But, can't delete a thread (as far as I know). 

But, thank you. 
:)

All good, it's a little confusing at first coming from windows, I once thought not being super user/root account 100% of the time was a bad thing! How things change :)

---

### Post by totalanonymity on 2011-03-17
Yeah, I'm reading about how sudo and gksudo can help me accomplish pretty much anything within Ubuntu without requiring persistent root access. So, shouldn't be a problem!

I really need to learn more about Linux!
These forums really are great, though. Everyone is really helpful and friendly, unlike most forums where the people are constantly rude and worse than unhelpful.

---

