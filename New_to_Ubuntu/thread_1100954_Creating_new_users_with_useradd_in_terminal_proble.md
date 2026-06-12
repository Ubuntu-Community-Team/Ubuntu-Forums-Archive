---
title: "Creating new users with useradd in terminal problem"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Rockey70 on 2009-03-19
Hey there, 

I'm using Linux in TAFE and to help with the subject I decided to install Ubuntu at home, one question in the text we have is to create some users via the terminal using useradd.

ie: useradd -p password emily

First this doesn't add the password for emily I have to create that via the menu in the manage users app, so no probs I create the password and it shows the user Emily having a home profile as /home/emily however if I try to log on with Emily it says something along the lines of the user has a home directory set but are unable to open it and it wont log in. I'm using 8.10. 

I am doing this logged in as the root which I managed to find out how to do via some web link as typing sudo everytime became a pain.

I'm using Ubuntu as an installed app through Windoze as I didn't want to mess up my partitions.

Any ideas?

Cheers

---

### Post by kanikilu on 2009-03-19
My understanding is that useradd does not create the home directory. It's easier to use adduser.

If you have to use useradd, you need to specify the home directory (which you have to create yourself and give appropriate permissions so the user can read it), set the shell, etc.

[http://www.debianadmin.com/users-and-groups-administration-in-linux.html](http://www.debianadmin.com/users-and-groups-administration-in-linux.html)

---

### Post by yeats on 2009-03-19
First of all, start with the manual:

```
man useradd
```

which will explain all the options.

> My understanding is that useradd does not create the home directory.

```
sudo useradd -m *username*
```

does add it

My typical method for adding a user is:

```
sudo useradd -m *username*
sudo passwd *username*
```

> I am doing this logged in as the root which I managed to find out how to do via some web link as typing sudo everytime became a pain.

This is not recommended in Ubuntu, as the entire security model is based on sudo.  You will probably benefit from this:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by erichmatt on 2009-03-30
I have run into a similar problem.  I want to be able to add a bunch of users to the server without having to type every name in.  I can make users using sudo useradd "bla bla bla" however I can't set the password.  -p does nothing that I can tell.  I read some were else that you have to type -p 'mkpasswd mypassword'  which I also haven't figured out to work

I can use passwd to change every password but that seems like a lot of work.  I can't find any way of setting or changing passwords via a script in ubuntu.


Eric Matt

---

