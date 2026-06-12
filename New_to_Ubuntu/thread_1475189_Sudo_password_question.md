---
title: "Sudo password question"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by held7over on 2010-05-06
Ubuntu 10.04 gnome

I was setting up a Ubuntu system for some friends, and was wondering why the sudo password can not be used in either a terminal or in a gui which is opened under a non sudo authorized user area?

I guess I am used to being able to su to root no matter where I am...but if I know the correct sudo password, doesn't that mean I could move to the sudo authorized user and then use the password anyway??? Why the complication?

---

### Post by seeker5528 on 2010-05-06
> **held7over said:**
> Ubuntu 10.04 gnome

I was setting up a Ubuntu system for some friends, and was wondering why the sudo password can not be used in either a terminal or in a gui which is opened under a non sudo authorized user area?

There is no such thing as "the sudo password", when it asks for the password, the user uses their own password. That's the point of using SUDO is that it gives more controlled ways of handing out access to things, without having to give everybody the root password.

It is possible to set sudo up so it uses a common password for different users that is different than their log-in password, but SUDO would still have to have some rules set up, either by individual or group about who is allowed to access some capability or group of capabilities.

It would defeat the purpose of SUDO if somebody that didn't have permission to use SUDO could use SUDO.

SU switches you to some other specified user account, or root if no user is specified. It doesn't provide any control, so whoever has the password for an account can switch to it.

I have not tried it, but there is a possibility that you could open a terminal window and do 'su *[some-other-user-with-permission-to-use-sudo]*' then from there do 'sudo -H su', then do your stuff that requires elevated permissions.

EDIT: I had a test user set up on this box, so I tried it, seems to work fine.

Later, Seeker

---

### Post by held7over on 2010-05-06
Thanks seeker5528!  That makes sense and your solution using su in a terminal to quickly change user will save me a lot of time! Thanks!

---

### Post by Sef on 2010-05-06
Ubuntu's wiki on [sudo]("https://help.ubuntu.com/community/RootSudo").

---

