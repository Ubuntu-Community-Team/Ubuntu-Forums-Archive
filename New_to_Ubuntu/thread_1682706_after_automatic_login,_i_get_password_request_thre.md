---
title: "after automatic login, i get password request three times"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Fabioamd87 on 2011-02-06
turn on pc, wait automatic login, I insert the password, the box reappear, I re-insert the passwrd, the box reappear, I re-re-insert the password and finally nothing happen.

i noticed that if I insert the password fastly just after automatic login I need to insert it just one time, but if I wait some second/minutes it need three times.

ubuntu 10.10

---

### Post by mcduck on 2011-02-06
That sound like it's asking you for the *keyring password*.

(the keyring is used to store passwords, like your wireless network apssword, encryption keys and such stuff from any application that wants to use it, keeping them safely in one place and secured when the keyring is locked)

As long as the keyring password and the login password are the same, and you use normal login (not automatic) the keyring will be unlocked automatically. Otherwise you need to give the keyring password to unlock it the first time some application tries to access some data from the keyring. You might even get asked for it couple of times if several applications try accessing it pretty much at the same time (which can often be the case with autostarting apps on login).

You pretty much have two options, either you can start using normal login, or you can remove the keyring password, which makes it store your passwords and encryption keys in unencrypted format but also allows the keyring to be accessed without having to unlock it. While the later approach is less secure, it's not really much of a difference if you are already using automatic login... :D

Here's how to remove the keyring password:
1. Go to System/Preferences/Passwords and Encryption Keys

2. Right-click the "Passwords:login"-keyring and select "Change Password"

3. Type in your current password, and leave the fields for new one empty.

---

### Post by Fabioamd87 on 2011-02-08
and if I want to understand why application need password? I have an open network so no password there, and in autostart there are gnome-do and nothing more...

---

### Post by mcduck on 2011-02-09
Well, quite many of the apps included by default will use the keyring, so it's a bit hard to say which ones are the ones that try too access it on  your system

Evolution, Empathy, Ubuntu-One, Network Manager, Gwibber, all the terminal server & remote desktop apps etc.

Pretty much any program that deals with user accounts, passwords, encryption keys or anything like that will be using the keyring to store such information.

---

### Post by Fabioamd87 on 2011-02-09
in my point of view, this is not my problem, but an architecture problem... i can't type my password 10-15 times for every application that need it...

---

### Post by migs73 on 2011-02-09
If you do as McDuck suggested earlier you won't have to. What has happened (I think, I'm no expert) is that your  keyring passwords have got out of synch. Once you have done as suggested you only need to enter it once.

---

### Post by mcduck on 2011-02-09
> **Fabioamd87 said:**
> in my point of view, this is not my problem, but an architecture problem... i can't type my password 10-15 times for every application that need it...

did you read my post? Once the keyring is unlocked, it's unlocked until you log out completely. You *don't* need to type it for every application that uses the keyring. And actually if you use normal login, or follow instructions  from my first post, you don't need to type it at all. Ever.

(the only reasons why the keyring manager might ask repeatedly for the password is that you are giving it wrong password and it can't unlock the keyring. Or if several apps request it exactly at the same time, before you have time to unlock it).

Anyway, not reading through my first post definitely doesn't count as architecture problem... :)

---

### Post by Fabioamd87 on 2011-02-09
but I don't want to remove the password, I just want to type it once...

---

### Post by sydbat on 2011-02-09
> **mcduck said:**
> Here's how to remove the keyring password:
1. **Go to System/Preferences/Passwords and Encryption Keys**

2. Right-click the "Passwords:login"-keyring and select "Change Password"

3. Type in your current password, and leave the fields for new one empty.On my 10.04, I find this under Applications > Accessories > Passwords and Encryption Keys.

I upgraded from previous versions (starting with 8.04 on this box). Could that be why I find this where I do? Maybe the OP has it in the same place as I do?

---

### Post by uRock on 2011-02-09
To make the key ring go away, open Network Manager by right-clicking the network icon and selecting Edit Connections, then click the Wireless tab if you are using wireless, then click your current network profile, then click Edit, then check the box in the lower left "Available to all users", then click Apply enter your password and you should not be asked for that password any more.

mcduck's first post explains how to edit those passwords. You can also delete them, but I haven't done this in 10.04, nor 10.10, so I am not sure if the process is the same any more.

---

### Post by mcduck on 2011-02-09
> **sydbat said:**
> On my 10.04, I find this under Applications > Accessories > Passwords and Encryption Keys.

I upgraded from previous versions (starting with 8.04 on this box). Could that be why I find this where I do? Maybe the OP has it in the same place as I do?

Yes, that's where it was in 10.04 and all previous versions. It was moved into System/Preferences in 10.10, which is what the OP said he's running in the first post.

> **uRock said:**
> 
mcduck's first post explains how to edit those passwords. You can also delete them, but I haven't done this in 10.04, nor 10.10, so I am not sure if the process is the same any more.
Works fine for both 10.04 and 10.10. :)

---

### Post by 3177 on 2011-02-09
Can't you set the keyring to start up before anything else (after necessary start up stuff) by going to start up programs and setting it as such? I believe startup programs is under administration.

---

### Post by Fabioamd87 on 2011-02-09
how?

ps: i've abled all users to use the wireless but nothing changed...

---

### Post by 3177 on 2011-02-09
sorry its not in administration. Go to System> Preferences> Startup Applications.

---

### Post by mcduck on 2011-02-09
> **3177 said:**
> Can't you set the keyring to start up before anything else (after necessary start up stuff) by going to start up programs and setting it as such? I believe startup programs is under administration.

It's not a question of starting the keyring, its about *unlocking* the keyring. (the keyring daemon is already started very early in the login process, and no matter how soon you start it still has to be unlocked)

So the solution *still* is to either make sure keyring password is the same as login password & using normal login, or removing the keyring password if you want to use automatic login.

---

### Post by 3177 on 2011-02-09
> **mcduck said:**
> Or if several apps request it exactly at the same time, before you have time to unlock it).



did you not read your own post?

---

### Post by uRock on 2011-02-09
> **3177 said:**
> did you not read your own post?
What is wrong with the post? No since being rhetorical.

---

### Post by 3177 on 2011-02-09
Im simply(trying)to give a solution for the original problem.
If the keyring is popping up over and over, as he said it was, it is probably, as mcduck said, a bunch of programs asking for permission before the keyring actually loads and unlocks everything. I dont appreciate someone telling me im wrong as I had this same problem in 9.10. 
To fix this I made sure that the keyring was first on the list of startup applications and voila.

---

### Post by Fabioamd87 on 2011-02-10
maybe the request for password shouldn't open another popup if one is still active?

---

