---
title: "Restrict specific user from sudo"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by phour10n3 on 2010-07-21
Sorry, I know the general topic is covered in many forums and websites but I cannot find any examples of exactly what I would like to do and I really dont want to mess up my sudoers file.

I would like to restrict one specific user from having sudo on my computer. The sudoers file right now reads (in part):
root    ALL=(ALL) ALL
...
...
...
%Domain\ Users ALL=(ALL) ALL

the user is included in the Domain (as I am). Also, would restricting him in this way keep him from having sudo when connecting via ssh?

Thanks

---

### Post by LowSky on 2010-07-21
Create an account for the user and don't add the user to the sudo group, simple as that... Ubuntu even has a simple GUI for adding users, these should help

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Paqman on 2010-07-21
> **phour10n3 said:**
> 
I would like to restrict one specific user from having sudo

No problem. Just go to System > Admin > Users & Groups and make sure that user is not in the admin group.

---

### Post by phour10n3 on 2010-07-21
Read through those pages... the user is already part of the "Domain" group. I suppose it would help if I described that this is a work machine and my desktop specifically but all of the users who log on get a home directory assuming that they are on a list on one of our servers as a valid user. Essentially anyone can log on with their username and password on any of our linux computers.

I do not have access to the Users and Groups on gnome (at least I don't know how to), but like everyone else I have sudo. I was hoping that there was a specific line that would specifically restrict this user from having sudo capabilities on my machine alone. Or possibly I could add his username on sudo but he needs to use the root pass?

---

### Post by gmargo on 2010-07-21
Yout can deny a single user, even if he is in the %Domain group.

Assuming this evil doer's name is issac, add the following line (with visudo), after the %Domain line.  This works since "last match wins" in the sudoers file.
```

issac ALL=(ALL) !ALL

```Note the bang (!) before the last ALL.

---

### Post by bodhi.zazen on 2010-07-21
> **gmargo said:**
> Yout can deny a single user, even if he is in the %Domain group.

Assuming this evil doer's name is issac, add the following line (with visudo), after the %Domain line.  This works since "last match wins" in the sudoers file.
```

issac ALL=(ALL) !ALL

```Note the bang (!) before the last ALL.

Either remove the evil user from the Domain group or if that is not possible use a different group for admin access and add the other users in.

If you are going to try the !ALL method, take care as listing users more then once in sudoers has unpredictable effects.

---

### Post by phour10n3 on 2010-07-21
Thanks all. I will look into changing the group, but I think it is through the network and out of my control. The bang method seems to work fine right now and hopefully it will not negatively affect anything.

---

