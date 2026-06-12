---
title: "Finding version / finding login password"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by n000buntu on 2009-05-30
I have two very basic unrelated questions:

1. On an computer with Ubuntu installed, how do I find what version it is? Seems like it should be obvious, I'm probably missing it.

2. When I first installed Ubuntu, I made a login for my wife, but she didn't really use it. Now she wants to, but we can't remember her password. I go to System>Administration>Users and Groups, click on her name and click on properties, but I can't see it.

---

### Post by bacardiandwatermelon on 2009-05-30
For the version number in terminal :-)
```
[FONT=verdana][SIZE=2][COLOR=#000000]cat /etc/issue[/COLOR][/SIZE][/FONT]
```

For the password... Did you click the unlock button first?

---

### Post by Tibuda on 2009-05-30
1. You have two ways to check it:
  a. System > About Ubuntu
  b. Type in a terminal: lsb_release -a

2. You can't see her password, but you can create a new password after you have unlocked the dialog.

---

### Post by Didius Falco on 2009-05-30
Hi

1. Open a Terminal shell (**Applications/Accessories/Terminal**) and type in ```
lsb_release -a && uname -r
```

This will tell you the version number/release, code name and kernel.

2. The easiest thing to do is to change the password. Go to **System/Administration/Users and Groups**. Click the **Unlock** button and enter your password. Highlight the account your wife is using and click the **Account** button. Tick the **Set Password by Hand** radio button and type the same new password in both boxes. Click **Okay** and **Close**.

Now your wife can log in using her new password.

Regards,

Didius

---

### Post by n000buntu on 2009-05-30
Thanks a lot, guys.:)

---

### Post by SunnyRabbiera on 2009-05-30
Another way to see the Ubuntu version is via the system monitor, located under system > Administration > system monitor

---

### Post by n000buntu on 2009-05-30
> **SunnyRabbiera said:**
> Another way to see the Ubuntu version is via the system monitor, located under system > Administration > system monitor

Thanks, Sunny. That method actually is better for me, since I have that running anyway. :)

---

