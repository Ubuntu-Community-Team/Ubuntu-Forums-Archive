---
title: "How to change password"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by StrobeWylan on 2010-11-14
When I installed 10:04 I should have come up with a more secure password. Lesson learned. I have searched how to change it but what I found I could not understand. I'm a newbie. Is there an easy way to change it?

---

### Post by hansdown on 2010-11-14
Welcome to the forum, StrobeWylan.

Ubuntu Geek has a good tutorial for changing it in 10.04.

[http://www.ubuntugeek.com/ubuntu-lucid-tiphow-to-change-currently-loggedin-user-password.html#more-5632](http://www.ubuntugeek.com/ubuntu-lucid-tiphow-to-change-currently-loggedin-user-password.html#more-5632)

---

### Post by uRock on 2010-11-14
System> Administration> Users and Groups. Once open, click on your screen name, then click the "change" button by Passord, then a Window will come up offering to change your password.

---

### Post by StrobeWylan on 2010-11-14
> **uRock said:**
> System> Administration> Users and Groups. Once open, click on your screen name, then click the "change" button by Passord, then a Window will come up offering to change your password.

When I try that I get the twirling curser, so far for about half an hour. Don't suppose that's normal, is it?

---

### Post by uRock on 2010-11-14
> **StrobeWylan said:**
> When I try that I get the twirling curser, so far for about half an hour. Don't suppose that's normal, is it?

Nope, that doesn't sound good.

---

### Post by dFlyer on 2010-11-14
Have you tried System/Preferences/About Me.

Upper right hand corner: Change Password.

---

### Post by MartyBuntu on 2010-11-14
Open a terminal and type

**sudo passwd**

After being prompted for your old password, hit ENTER and you'll be given instruction to enter a new password of your chosing.

---

### Post by StrobeWylan on 2010-11-15
Tried all the above and still got the 'twirl to eternity' syndrome.

When I tried:

> **MartyBuntu said:**
> Open a terminal and type

**sudo passwd**

After being prompted for your old password, hit ENTER and you'll be given instruction to enter a new password of your chosing.

It confirmed that I had changed it but when I tried it out could only log on with the old one.
    Maybe I should just come to love my old one.

---

### Post by StrobeWylan on 2010-11-15
I should say thank you for all your attempts at helping. Thanks to hansdown for the welcome to the forum. I did go to the tutorial and got the same results. It mentioned a work around if the new password resembled the old (which it did in my case). I tried that and still failed. I'm letting things be for now. Maybe later when I have more time I'll tackle this again.

---

### Post by sisco311 on 2010-11-15
The **sudo passwd** command enables the root account, which is not a good idea. To (re-)lock the root password run:
```
sudo usermod -p '!' root
```

In order to change your user password, you have to run:
```
passwd
```

---

### Post by StrobeWylan on 2010-11-15
> **sisco311 said:**
> The **sudo passwd** command enables the root account, which is not a good idea. To (re-)lock the root password run:
```
sudo usermod -p '!' root
```

In order to change your user password, you have to run:
```
passwd
```

I have wondered about this. Does anyone else have an opinion? Just would like to see what others think as well.

---

### Post by yetiman64 on 2010-11-15
> **StrobeWylan said:**
> I have wondered about this. Does anyone else have an opinion? Just would like to see what others think as well.

I agree that [COLOR=Black]sisco311[/COLOR] is completely correct and that is why you still needed the old password to get in. 

However if you successfully put a password in with the command [COLOR=Black]MartyBuntu[/COLOR] posted, your root account is now enabled and to disable it (the default setup) run the command [COLOR=Black]sisco311[/COLOR] posted (check out link #4 in my sig "RootSudo" community documentation to confirm the command).

Using [[COLOR=SeaGreen]--this link--[/COLOR]]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account") will take you to the specific command in the documentation (it is the same command sisco311 posted). 

Having an enabled root account in Ubuntu is a very bad idea and usually totally unnecessary in view of sudo use. I realize you may have **unintentionally** enabled the root account.

Cheers from yetiman64.

---

### Post by StrobeWylan on 2010-11-15
Ok, I'll give it a try.

Thanks to both.

---

### Post by StrobeWylan on 2010-11-15
And the grand prize goes to sisco311, with help from yetiman64.:)

That worked. Wonder why the other ideas didn't.:confused:

---

