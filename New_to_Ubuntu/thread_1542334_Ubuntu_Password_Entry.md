---
title: "Ubuntu Password Entry"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by skaarr on 2010-07-30
Not really a problem as such, I'm simply curious.
When I enter my password to log on to my account, if I enter it incorrectly there is a delay of a couple of seconds before I can enter it again, where as if I enter it correctly, it logs in straight away.

Can anyone explain the delay?

---

### Post by sydbat on 2010-07-30
> **skaarr said:**
> Not really a problem as such, I'm simply curious.
When I enter my password to log on to my account, if I enter it incorrectly there is a delay of a couple of seconds before I can enter it again, where as if I enter it correctly, it logs in straight away.

Can anyone explain the delay?It is likely checking and rechecking the password against the saved password file, making sure it is incorrect before prompting you to try again. It is also logging the incorrect attempt and counting how many incorrect attempts are left before locking the computer for a specified time.

That, or it is messing with you, treating you like someone trying to crack your computer and making it look like it will log in with no problem...then popping up the login prompt while snickering to itself...

---

### Post by jrothwell97 on 2010-07-30
It's a simple mechanism against what's known as "brute force" attacks, where an automatic system of some form tries millions of passwords, one after the other, in the hope of happening upon the right one.

Brute force attacks are slow and inefficient anyway, and adding an additional delay of a second or two makes them virtually impractical.

---

### Post by endotherm on 2010-07-30
> **jrothwell97 said:**
> It's a simple mechanism against what's known as "brute force" attacks, where an automatic system of some form tries millions of passwords, one after the other, in the hope of happening upon the right one.

Brute force attacks are slow and inefficient anyway, and adding an additional delay of a second or two makes them virtually impractical.

we have a full disk encryption system at work that really punishes you for misentry. on the second bad entry, it starts adding a 1 minute pause between attempts, and with every subsequent failure, increases the time by an additional minute. after 5 bad attempts its up to 3 minutes... and then your account is disabled.

---

### Post by sisco311 on 2010-07-30
If you want to learn more, check out: [http://en.wikipedia.org/wiki/Linux_PAM](http://en.wikipedia.org/wiki/Linux_PAM)

The default action for the pam_unix  module is to request a delay-on-failure of the order of two seconds.

```

man pam_unix
man pam_tally
```

---

### Post by skaarr on 2010-08-01
Thanks for all your replies.
I've never misentered my password twice in a row, but I might go try it now.
Thanks again all, you've been very helpful.

---

