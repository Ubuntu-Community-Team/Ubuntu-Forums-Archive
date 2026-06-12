---
title: "Can't ssh in as new user"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by gary441 on 2007-07-11
Hello all,
I made a new user on a fiesty server box, but I can't ssh into that box as that user.  I can ssh as a user that I made during the install.  I can log-in as the new user while sitting at the terminal, so I know the username and password is working.
When I try to ssh in as the new user, it asks me for the password again, then after so many times fail2ban likes to block my IP address.

Any ideas why I can't ssh in as the new user, but the original user works fine?

Thanks for all the help.


Gary :)

---

### Post by PgR on 2007-07-11
Does /etc/ssh/sshd_coonfig contain AllowUsers <original_user>?

---

### Post by gary441 on 2007-07-11
PgR,
Thanks alot.  That was the magic trick.
I don't usually add users to my servers, so I don't think I've ever had to add that.

I added a user like this:
AllowUsers mike john  
to the sshd_config file, then restarted ssh and it worked.

Thanks again.
Gary

---

