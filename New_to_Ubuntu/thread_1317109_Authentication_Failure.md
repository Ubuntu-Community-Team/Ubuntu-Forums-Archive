---
title: "Authentication Failure"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by mckelliget on 2009-11-06
I have installed UBUNTU alongside Windows XP
 
When I try to log in to UBUNTU it says "Authentication Failure"
 
I am 100% certain that I am typing in my password correctly and that it is the same password that I entered (twice) during the installation.
 
So obviously something got corrupted.
 
Any suggestions?

---

### Post by CJ Master on 2009-11-06
Some more detail would be helpful. Are you using WUBI, or did you install it by disk? Did check the disk to make sure it didn't corrupt when you burned it? What version of Ubuntu are you using?

---

### Post by Darce on 2009-11-06
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by mckelliget on 2009-11-06
I reset password OK
 
Then when I tried to log in from the prompt it said
 
keyctl_search : Required key not available.....
 
When I went to the normal login screen it sais
 
Could not update ICEauthority file/home/mckelliget/.ICEauthority
......

---

### Post by ChronoSphere on 2009-11-06
I have the exact same problem -- and no solution yet. See my post: [http://ubuntuforums.org/showthread.php?t=1234087](http://ubuntuforums.org/showthread.php?t=1234087)

If I install 8.10 the password works. If I install 9.04 or above, then it doesn't. Something with authentication changed between Intrepid and Jaunty. Resetting the password doesn't fix this problem.

---

