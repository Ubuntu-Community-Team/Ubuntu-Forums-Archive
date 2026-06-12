---
title: "Users and root"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-01-31
So I don't fully understand why some file are for the root user and some are for me that is my account. I do get that some times I have to use sudo and some times I have to change ownership or write permission. 

My question is why doesn't the default login account have full control and why should I not change it so I can?

---

### Post by jimmy the saint on 2009-01-31
It is for security and to prevent you, or someone who gains access to your account, from fragging your system.

Check out the "root policy login" link in my sig for a very good explanation of these permissions and why Ubuntu is built the way it is (using sudo)

---

### Post by sirebral on 2009-01-31
You probably should not be changing ownership and permissions.

Linux is Unix like, as is MacOSX.  Surprise, in the recent news the virus that hit Macs required the users install it, unlike something like the Conficker... 

The password protection is a pretty good layer against unwanted programs unpacking and running on your system.  If you change ownership and permissions you are opening doorways to those files that may require protection.

---

