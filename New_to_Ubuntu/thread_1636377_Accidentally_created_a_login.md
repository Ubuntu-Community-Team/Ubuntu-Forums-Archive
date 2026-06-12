---
title: "Accidentally created a login"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by PaulXUb on 2010-12-03
I've been playing around with Ubuntu after I installed it, and must have accidentally created a login.  I don't recall ever entering a name or a password, but now my login is asking for me to enter a username.  Is there anything I can do to get out of it?

---

### Post by sikander3786 on 2010-12-03
There must have been a user account that you previously used to login Ubuntu?

That might have been configured to auto-login but you definitely needed the password to gain root privileges while doing some certain task like installing drivers, accessing/modifying system files, changing time etc. Do you remember that password?

If you want to reset your password, follow this guide.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Yougo on 2010-12-03
During installation, you were asked to fill in some details, such as your full name. it then suggested a username, usually your first name in lowercase letters. maybe you typed a custom username. below that you typed a password. there was also a checkbox for the option to log in automatically.

now what i think happened is that you disabled the automatic login.
here's to set it up again:

Open System &#8594; Administration &#8594; Login Screen.

Press Unlock and type your password to unlock the settings

Check Login as.

Choose a username from the drop down list to login as.

Press Close.

Changes will be applied on re-boot.

---

### Post by PaulXUb on 2010-12-03
I've ran Ubuntu using a persistent USB drive.  I don't think I ever had to log in before.

---

### Post by julio_cortez on 2010-12-03
> **Yougo said:**
> Open System &#8594; Administration &#8594; Login Screen.

Press Unlock and type your password to unlock the settings

Check Login as.

Choose a username from the drop down list to login as.

Press Close.

Changes will be applied on re-boot.
Just a thought: if he is locked out of the system, would there be a way to do this same work via a Live CD?
Just in case he's asked for credentials upon login and he doesn't know them, because from what I read I doubt he could access the ***System*** menu.

---

### Post by sikander3786 on 2010-12-03
> **PaulXUb said:**
> I've ran Ubuntu using a persistent USB drive.  I don't think I ever had to log in before.
Ahhh. You needed to mention that in your first post.

I don't know much about persistent USB. Did you try the default login name 'Ubuntu' with a blank password?

Anyways, it should not ask you to login unless you configured it to...

---

### Post by PaulXUb on 2010-12-03
> **julio_cortez said:**
> Just a thought: if he is locked out of the system, would there be a way to do this same work via a Live CD?
Just in case he's asked for credentials upon login and he doesn't know them, because from what I read I doubt he could access the ***System*** menu.

You are correct.  I cannot access the system.

---

### Post by PaulXUb on 2010-12-03
Thank you for your help.  I realize what I did now.  I checked the option to allow 10 seconds for anyone to log in first.  It automatically logged in after 10 seconds.

---

### Post by Yougo on 2010-12-03
glad you didn't disable it completely :) those were some anxious 10 seconds right? ;)

now that you're in, maybe you could change your username and password to something you remember (aside from disabling login again) so when this ever happens again, or when you need to log in from terminal, at least you can.

---

