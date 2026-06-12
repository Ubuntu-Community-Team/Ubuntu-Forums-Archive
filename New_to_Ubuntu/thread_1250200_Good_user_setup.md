---
title: "Good user setup"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by dcccc on 2009-08-26
Hi I'm new to Ubuntu so I was wondering what kind of user setup I should use. I'm the only one who will use the computer, aside from visiting friends etc. So which of these two are the most secure and convenient?

First setup:
1. User with admin privileges, (the one created during install) which would be used for administration.
2.  User without admin privileges, used as my personal account for day to day use.
3.  User without admin privileges, which would be a guest account for others to use.

Second setup:
1. User with admin privileges, (the one created during install) which would be used for administration and as my personal account.
 2.  User without admin privileges, which would be a guest account for others to use.

Or do you have any other recommendations?

---

### Post by compiledkernel on 2009-08-26
The Second setup is probably the most viable for any common use, dccc. I guess if your really really security concious and you dont want even sudo access for anyone but yourself, you could go with Scenario one, but just for an everyday desktop, it seems a little overkill. 

It depends on how many people are going to use the machine.

---

### Post by jrothwell97 on 2009-08-26
Welcome to the Ubuntu forums!

I'd recommend the second setup: Ubuntu works differently than Windows, because 'administrator' accounts only get administrator privileges when actually doing something *administrative*. Therefore, you should be safe as long as you use a strong password.

Also, if you're using Ubuntu 8.10 or later, you can probably make do without an unprivileged guest account, because Ubuntu provides one automatically (you select 'Guest session' from the user list on the top panel, and a guest account is automatically created.) The contents of the guest account are removed on logout.

---

### Post by dcccc on 2009-08-26
Thanks for your answers! I did not know about guest session but that seems like a good idea, I think I will use second setup but instead of a guest user I will use guest session.

---

