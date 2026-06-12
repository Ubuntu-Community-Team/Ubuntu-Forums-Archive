---
title: "Samba restrict access too certain sub-directory"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by alex422 on 2015-08-05
Hi all

I am just setting up my Samba server and I am wondering how to restrict access too certain sub-directories in the root share

So if my root share is

[COLOR=#ff0000]root[/COLOR] and in the [COLOR=#ff0000]root[/COLOR] share I have 6 directories labelled [COLOR=#0000cd]dir1, dir2, dir3, dir4, dir5, dir6

[/COLOR]Now if I want Bob to have access to [COLOR=#ff0000]root[/COLOR][COLOR=#0000cd], [/COLOR]but only able to see[COLOR=#0000cd] dir1, dir2, dir5


[/COLOR]How would I go about stopping him from getting access to[COLOR=#0000cd] dir3, dir4, dir6 [/COLOR]and not being able too see them either[COLOR=#0000cd]

[/COLOR]Thank you in advance

---

### Post by cj13579 on 2015-08-05
Welcome to the Forum! The below code does what you need, but you need to make sure that the server side permissions match what you want to see in samba:

```

[share]
  valid users = user1 user2 @group1 @group2
  hide unreadable = yes

```

This stuff is all in the documentation: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

EDIT: Updated with hide unreadable option and said hello!

---

### Post by alex422 on 2015-08-05
> **cj13579 said:**
> Welcome to the Forum! The below code does what you need:

```

[share]
  valid users = user1 user2 @group1 @group2
  hide unreadable = yes

```

This stuff is all in the documentation: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

EDIT: Updated with hide unreadable option and said hello!

Hi Chris

Hi to you to :D

I read that using the hide unreadable though would still allow people too see the folder on the windows machine if they had "show hidden files and folders" enabled.

Is that correct ?

---

### Post by cj13579 on 2015-08-05
Nope, that should hide them. If you were to use the "hide files" option then I believe that you would see the behaviour that you suggest (though the icon would be transparent as if it was a hidden folder).

---

### Post by alex422 on 2015-08-05
> **cj13579 said:**
> Nope, that should hide them. If you were to use the "hide files" option then I believe that you would see the behaviour that you suggest (though the icon would be transparent as if it was a hidden folder).

Ok great I will try that 

Having other issues now, do not seem to be able to write or create in the share from the windows machines :/

---

### Post by alex422 on 2015-08-05
Nvm sorted that now

Do I just set the unreadable permission with CHMOD ?

---

