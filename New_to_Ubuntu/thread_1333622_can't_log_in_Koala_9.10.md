---
title: "can't log in Koala 9.10"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by zhanglini on 2009-11-21
I installed 9.10 today and logged in a few times successfully.

But this time, every time I enter the password (both my account and the guest account), it would proceed with the process then return back to the login screen.  I don't think I had the wrong password, because I intentionally enter the wrong pw, it would tell me pw was wrong.

So now I am using my live CD.

How do I fix this with my live CD?

Thank You In Advance!!!

---

### Post by XCan on 2009-11-22
It seems like something is crashing when it initializes your session. What was the last thing you changed? 

I would first create a new user, try and login with that one. This will check if it's a system error or configuration error on your original user only. If it's a configuration error, you'll need to think hard on what you did the last time it worked, or start digging in the logs.

---

### Post by zhanglini on 2009-11-23
> **XCan said:**
> It seems like something is crashing when it initializes your session. What was the last thing you changed? 

I would first create a new user, try and login with that one. This will check if it's a system error or configuration error on your original user only. If it's a configuration error, you'll need to think hard on what you did the last time it worked, or start digging in the logs.

Thanks Xcan,

I ended up reinstalling 9.04, 9.04 had been in stable use for a while and Koala seems to be too much trouble to me (a bad first impression).
I did delete a lot of things (too many to remember and list here!) when I first installed Koala, but btwn the last time I successfully logged in and the times I couldn't, I dont believe I changed anything. Since I am pretty new I doubt I could use your method --- adding a new user, when on live CD.

Thanks

---

### Post by Scholar-code on 2009-11-23
> **zhanglini said:**
> Thanks Xcan,

I ended up reinstalling 9.04, 9.04 had been in stable use for a while and Koala seems to be too much trouble to me (a bad first impression).
I did delete a lot of things (too many to remember and list here!) when I first installed Koala, but btwn the last time I successfully logged in and the times I couldn't, I dont believe I changed anything. Since I am pretty new I doubt I could use your method --- adding a new user, when on live CD.

Thanks
9.04 is quite stable to me, I did upgrade to 9.10 and I had few Issue, then I did give a clean install instead of upgrading, and now it fine and quite stable from past few days.

As far as login issue is concern, did you tried changing the password. I had this little issue with 9.04 and get into recovery console and droped a root shell and changed the user password and it was fine. [ In case, we forget/oversight the password], give a try :]

---

### Post by XCan on 2009-11-23
> **zhanglini said:**
> Thanks Xcan,

I ended up reinstalling 9.04, 9.04 had been in stable use for a while and Koala seems to be too much trouble to me (a bad first impression).
I did delete a lot of things (too many to remember and list here!) when I first installed Koala, but btwn the last time I successfully logged in and the times I couldn't, I dont believe I changed anything. Since I am pretty new I doubt I could use your method --- adding a new user, when on live CD.

Thanks

Ah, that's a pity. :) Adding a new user is very easy, next time you want to try it, just enter the GRUB booting menu (the one showing up before Ubuntu actually loads) and select the recovery mode. Once in there you can simply type
```

sudo adduser username 
sudo passwd username

```
and follow the on-screen instructions. :)

---

### Post by zhanglini on 2009-11-23
Thanks guys,
I really need to remember some of the commands.
It does not look THAT hard!

Have a great week!

---

