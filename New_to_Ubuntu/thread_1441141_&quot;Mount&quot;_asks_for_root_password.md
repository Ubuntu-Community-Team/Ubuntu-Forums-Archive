---
title: "&quot;Mount&quot; asks for root password"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by mak_20789 on 2010-03-28
Hi,
      I ve installed Gmount to play ISO files. I followed steps told in some article and opened ISO file in 1st box, opened empty folder I created on my desktop in the 2nd box and clicked on "Mount" and its asking me for root password. Now one thing I know about Ubuntu is this p/w is very imp. So is it a usual thing for Mount to need my password or should I just stay away from it?

Thank you in advance.

---

### Post by egalvan on 2010-03-28
When Linux needs to do Very Important Things, it will ask for the root password...

In the case of Ubuntu, the root account is disabled by default,
so this mechanism is handled through 'sudo', 
which is in reality asking for *your* log-in password.

Just type in your log-in password. All is fine.

Note that nothing will be displayed, not even stars or dashes,
this is to prevent someone else from counting the number of characters in your password (a very important piece of the puzzle when it comes to password cracking)

---

### Post by readycarpenter on 2010-03-28
this is fine, if you opened gmount and then it prompts for pass then no worries, the thing you need to worry about is being promted for password when you did not initiate it

hope this helps 
cheers

---

### Post by mak_20789 on 2010-03-28
Thank you.

---

