---
title: "Authorisation failed - Help"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by dave66 on 2009-04-06
Hi,

I'm a newbie Linux/ubuntu user.

I recently got a Dell Mini-9 with Ubuntu 8.04

It was bugging me that each time I booted (and logged in) that I was being asked to enter a password to unlock the Keyring so that the PC would logon to wireless network.

So I foolishly added 

@include common-pamkeyring

to /etc/pam.d/gdm

I found in the following post:

[http://ubuntuforums.org/showpost.php?p=3605925&postcount=4](http://ubuntuforums.org/showpost.php?p=3605925&postcount=4)

That solution was to remove "@include common-pamkeyring" (which I had guessed) however my problem is, when I try 

sudo gedit /etc/pam.d/gdm

I get 

"cannot open display"

I tried using Nano, but it does not seem to be installed as I get:

sudo: nano: command not found

If I try use it not as sudo I get

bash: nano: command not found

So it looks like both gedit and nano are not runners for me.

How the heck can I get rid of that darn line from the end of /etc/pam.d/gdm ?

Please help, I need to get this PC running for tomorrow  :eek:

---

### Post by taurus on 2009-04-06
See if you have vi text editing on your machine.

```
sudo vi /etc/pam.d/gdm
```
You can remove a line with dd and if you want to add something to it, you need to press i to get into the insert mode.  Once you are done inserting, press Esc and save it with 

```
:wq!
```

---

### Post by naveedmurtuza on 2009-04-06
hi dave66

first of all i am myself a linux/ubuntu newbie

and if i am not wrong gdm is graphical disply manager guessing from the error "cannot open dispaly"

try going to command prompt ctrl+alt+f3

then

sudo vi /etc/pam.d/gdm

in vi press i to start editing once finished press Esc followed by (colon)
:wq      that is write & quit

aah! too late i guess  ...

---

### Post by dave66 on 2009-04-06
Thanks guys!!

vi worked a treat, phew

As an unexpected bonus, it would now appear that when I log in, it's not looking for the password for the keyring like it was before - go figure. That's how I thought it was supposed to work but wasn't.

Thanks for the fast replies, I can rest easy now.

---

