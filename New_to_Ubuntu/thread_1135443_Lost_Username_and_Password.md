---
title: "Lost Username and Password"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by jbehl on 2009-04-24
I upgraded to 9.04 last night and fished the install this morning. I do not remember ever setting up a username or password when I installed 8.10. I tried all of my normal logins and passwords, but nothing worked. So I'm stuck at the login splash screen.

Is there some other way or something in options I can change for it not to ask for username/password on boot up. 

How can I recover my username/password?

---

### Post by nandemonai on 2009-04-24
You must have setup a user and password. It's impossible to not have at least one user (in essence anyway).

I'm assuming you setup automatic login.

What you'll need to do is boot into recovery mode.

Then:

```
ls /home/
```

That will list the user directories. Whatever name is in there is the name of your user.

Then:

```
sudo passwd username
```
*username being the name you saw in /home/

Set a new password. Reboot and you should be able to login.

---

### Post by jbehl on 2009-04-24
> **nandemonai said:**
> You must have setup a user and password. It's impossible to not have at least one user (in essence anyway).

I'm assuming you setup automatic login.

What you'll need to do is boot into recovery mode.

Then:

```
ls /home/
```

That will list the user directories. Whatever name is in there is the name of your user.

Then:

```
sudo passwd username
```
*username being the name you saw in /home/

Set a new password. Reboot and you should be able to login.

Great thanks. I'm sure I had it set up for auto login, I just forgot the username I used. If my user name was the name of the folder in my home folder, I'm good. I remember that. 
I'll give it a try when I get home.
Thanks-

---

### Post by tom56 on 2009-04-24
What password did you enter to install the upgrade? That's your password.

To set up automatic login, go to System->Administration->Login Window and go to the "Security" tab and select "enable automatic login".

---

### Post by jbehl on 2009-04-24
> **tom56 said:**
> What password did you enter to install the upgrade? That's your password.

To set up automatic login, go to System->Administration->Login Window and go to the "Security" tab and select "enable automatic login".

I know the sysadmin password, I figured it should be the same. For some odd reason I used a completely different username, something I never use. That is what I couldn't remember.

---

### Post by tom56 on 2009-04-24
There's no such thing as a sysadmin password. Instead, it asks for your own password to give you sysadmin (or "root") priveleges. This is the reason why every user has to have a password. Glad you sorted it out :)

---

### Post by jumper2 on 2009-04-24
Hi Guys

I also have just upgraded from 8.10 to 9.4.  

The upgrade was successful but it will not accept the password that I used for 8.10.

I booted in Recovery Mode but found no option for "Code".

Any suggestions other than to download to disk and completely reinstall?

---

