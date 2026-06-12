---
title: "samba users"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by tjtansey on 2007-02-08
How do you designate samba users to be able to access your shared folder from a home network?

---

### Post by gradedcheese on 2007-02-08
I only know how to do this at the shell, so if you're ok with that I can help.  You'll need to edit your /etc/samba/smb.conf file and also add the users to samba (with "sudo smbpasswd -a user_name") once you've added them as users on your machine.

Here's what I usually do, someone else might suggest an easier approach, which would be good.

1) make a Linux account for the user in question:

sudo adduser user_name

2) add them to samba users and set their samba password:

sudo smbpasswd -a user_name

3) configure samba.  In /etc/samba/smb.conf (which you edit with sudo privileges) you'll find that shares are formatted like this:

```

[share_name_goes_here]
   comment = All Users
   path = /path/to/the/share
   valid users = @users
   force group = users
   create mask = 0660
   directory mask = 0771
   writeable = yes

```

This would allow any valid user access.  If you change the valid users line to instead list the user names you want, then just those people will have access.

4) after making your changes, restart the samba server:

sudo /etc/init.d/samba restart

If you're having trouble, take a look at /etc/group and make sure that the 'users' group lists the user names you added too (that is, if you 'force group' like I did).  I hope that helps.

---

### Post by tjtansey on 2007-02-08
I think I can muddle though it now.  You've come to the rescue again thanks

---

