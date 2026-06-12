---
title: "I get asked for a password when trying to use guest account"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by learningcurb on 2009-10-10
So I get this problem when I'm trying to use the guest account on my Jaunty install.  Everything works fine the first time I log into the guest account, but if I happen to log off of the guest account then try to log back in, I get sent to the main login screen and Ubuntu asks for a password.

Does anyone know what's wrong and how I can fix this?

---

### Post by cariboo on 2009-10-10
The guest account that is set up by default can only be accessed from your user desktop. You must enter a password to access your own account when logging out from the guest account.

If you want to have a guest account, without having to go through your own dwsktop, create a new user with just basic permisiions. You should still create a strong password, as many systems have been cracked by using guest as a user and guest as a password.

---

### Post by learningcurb on 2009-10-11
Hmm, I think I need to explain the problem more clearly.  Basically here's the problem:

1. I log into my normal account, then I let a room-mate hop on the computer for a minute to check their email via the guest account.

2. They finish checking email and log off of the guest account, I resume using the computer from my normal account.

3. Later that day, another room-mate wants to check their email for a bit.  This time when attempting to access the guest account, I get sent to the main login screen and asked for a password.  Of course the guest account has no password as far as I know, so it becomes impossible to use the guest account.

It is possible to get back into the guest account, by logging out of my account and logging back in, and then switching to the guest account again, but having to log in and log out is kind of annoying.  Also, I would rather not create user accounts for my roommates on my computer.  It seems like either I've misconfigured something somewhere or I've run into a bug, but I'm not sure what it is.  Does anyone have a clue about what's wrong?

---

