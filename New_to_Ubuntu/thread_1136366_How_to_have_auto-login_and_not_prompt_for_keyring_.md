---
title: "How to have auto-login and not prompt for keyring password for wireless access"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by dugh on 2009-04-24
What is the official way to get auto-logins and wireless working without prompting for the keyring password?

I've seen other threads on this, but no solution:
[http://ubuntuforums.org/showthread.php?t=463639&page=6](http://ubuntuforums.org/showthread.php?t=463639&page=6)
This is for a kid to use.

---

### Post by m_2009 on 2009-04-25
For auto-login go to STSTEM > ADMINISTRATION > LOGIN WINDOW. Then select the security tab and you should see a check box for automatic login.

As for wireless access, when i clicked on the wireless icon in the notification area (the strength meter, looks like a graph), it should give you a list of all available wireless networks. I selected mine, and it asked me for the wireless key. I entered it and have never been asked for it again, and it auto connects. Is that what you tried?

---

### Post by dugh on 2009-04-25
I think I got it.  I right clicked the wireless applet, went to edit connections->wireless tab and then editing the wireless connection to check "available to all users".

See Collin's comment and my response on this bug report:
[https://bugs.launchpad.net/gnome-keyring/+bug/137247](https://bugs.launchpad.net/gnome-keyring/+bug/137247)

---

### Post by johnnybirdman on 2009-04-25
> **dugh said:**
> I think I got it.  I right clicked the wireless applet, went to edit connections->wireless tab and then editing the wireless connection to check "available to all users".

See Collin's comment and my response on this bug report:
[https://bugs.launchpad.net/gnome-keyring/+bug/137247](https://bugs.launchpad.net/gnome-keyring/+bug/137247)

Thanks for this info.  I know that a lot of people have been looking for this solution for a long time.  I don't know how long that setting has been there but thanks for pointing it out.
I can confirm this works as well.
J.

---

### Post by sirjoebob on 2009-04-25
Thanks for this solution. I have been trying to find this for a while and decided to look it up again.

---

### Post by carrucha on 2009-06-02
I was very excited to see this solution.  I got it to work without much difficulty on my new 9.04 install I'm putting together.  Went to go do the same on my "production" setup... couldn't find the option any more!  It's an 8.10.  I get to the edit tab and then there is no option to check for "available to all users".  I see a checked "connect automatically" and an unchecked "system setting" which won't take if I select it.

Do I need to turn something else on?

---

### Post by johnnybirdman on 2009-06-02
> **carrucha said:**
> I was very excited to see this solution.  I got it to work without much difficulty on my new 9.04 install I'm putting together.  Went to go do the same on my "production" setup... couldn't find the option any more!  It's an 8.10.  I get to the edit tab and then there is no option to check for "available to all users".  I see a checked "connect automatically" and an unchecked "system setting" which won't take if I select it.

Do I need to turn something else on?

I think I understand what your asking, and I believe the answer is that this is/was not in prior versions.
J.

---

### Post by carrucha on 2009-06-02
Well the problem is there for me in the older version, so how do I fix it?  Right now I have to connect manually all the time or I'm not online.

---

### Post by mnmleon on 2009-06-27
Omg thank you! Sticky

---

