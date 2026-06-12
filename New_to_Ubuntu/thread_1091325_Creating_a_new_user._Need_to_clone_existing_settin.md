---
title: "Creating a new user. Need to clone existing settings but not admin."
date: 2009-03-09
forum: New to Ubuntu
---

### Post by philinux on 2009-03-09
New to this as before I've only had single user machines. How do I create a new user but with all the settings, i.e look and feel, I've got now except admin rights. I.e. a desktop user.

Activating the guest account gives a default desktop. New user is a newbie ex windows user so I dont want to have them fiddle to get it to look the same as I've tweeked my user.

---

### Post by gn2 on 2009-03-09
Something to try, don't know if it will work for you, but it has for me in the past:

System > Administration > Users and groups, set up your new user as a "Desktop" user.

Then: Alt+F2 and run gksudo nautilus 
Then copy and paste the .hidden config files and folders in your /home to the new user's /home

(You might not want to copy across your e-mail application's .hidden folder)

---

### Post by 3rdalbum on 2009-03-09
It's easy. Copy all the hidden folders in your home directory into /etc/skel - the hidden folders contain your desktop settings. Now create the new user account. The contents of /etc/skel will be copied into the new user's home directory. Presto!

(EDIT: Don't copy any folders that contain personal information, such as keyrings, e-mail settings, Pidgin settings)

---

### Post by philinux on 2009-03-09
/etc/skel thats a new one on me. Thanks i'll give it a go. 

Ahh I see it contains the examples folder.

---

### Post by hyper_ch on 2009-03-09
if you just want to set it up for one new user then I would not copy it to /etc/skel but just make a copy of your home folder and then chown it accordingly.

---

### Post by philinux on 2009-03-09
> **hyper_ch said:**
> if you just want to set it up for one new user then I would not copy it to /etc/skel but just make a copy of your home folder and then chown it accordingly.

I'd copy everything except the thunderbird folder I reckon
I suppose I'll have to watch the .dmrc file permissions if I do it this way.

---

### Post by cat2005 on 2009-08-29
> **3rdalbum said:**
> It's easy. Copy all the hidden folders in your home directory into /etc/skel - the hidden folders contain your desktop settings. Now create the new user account. The contents of /etc/skel will be copied into the new user's home directory. Presto!

(EDIT: Don't copy any folders that contain personal information, such as keyrings, e-mail settings, Pidgin settings)


Bump.

I am in the same boat.  Has anyone tried the above suggestion?  How well did it work?

---

### Post by abjangam on 2009-08-29
my system was good but I went in the system admin to add other users of my pc
and I make changes like
deleted home from group
change password
new user
delete user of my name

before it was ashwn@ashwin-laptop

but now it says I have no name@ashwin-laptop

after signout I cant access my PC

please help me

---

### Post by abjangam on 2009-08-29
my system was good but I went in the system admin to add other users of my pc
and I make changes like
deleted home from group
change password
new user
delete user of my name

before it was ashwn@ashwin-laptop

but now it says I have no name@ashwin-laptop

after signout I cant access my PC

please help me

---

### Post by abjangam on 2009-08-29
> **abjangam said:**
> my system was good but I went in the system admin to add other users of my pc
and I make changes like
deleted home from group
change password
new user
delete user of my name

before it was ashwn@ashwin-laptop

but now it says I have no name@ashwin-laptop

after signout I cant access my PC

please help me

I  can access now my account with the guest user which i add in last time when i went in users and groups and deleted my parental group ashwn

so how could i get my reall name user

please help me

---

