---
title: "Changing root password"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by dominiquepoole19900 on 2010-08-23
How do I change root password in fedora 10.4

---

### Post by silverglade00 on 2010-08-23
> **dominiquepoole19900 said:**
> How do I change root password in fedora 10.4

Why are you asking this on Ubuntu forums?

But since we are so helpful here... Log in as root then run this command in the terminal:

```

passwd

```

It will ask for your new password twice. It will not show anything while you type, so you need to type carefully.

---

### Post by Elfy on 2010-08-23
[http://fedoraforum.org/](http://fedoraforum.org/)
[http://docs.fedoraproject.org/en-US/index.html](http://docs.fedoraproject.org/en-US/index.html)

Please go to their forums or documentation.

Edit @ OP - to clarify - are you sure you are talking about fedora? Or do you mean ubuntu 10.04. If it is in fact ubuntu we can re-open the thread - PM me and I will - or use the report abuse button and ask to have it re-opened

If you mean ubuntu then the root password is disabled by default but you can change your password (which is used by sudo as opposed to su) by running in recovery mode - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

