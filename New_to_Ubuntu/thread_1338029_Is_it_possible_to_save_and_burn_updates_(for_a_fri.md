---
title: "Is it possible to save and burn updates (for a friend)"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by MisFitt on 2009-11-26
Hi,
I hope this is possible:
I have a friend who lives in the bush with a very limited internet service and I want to not only send him 9.04 and 9.10 but hopefully,somehow,the updates along with programs.
So is it possible to download and save and burn updates?
Fingers crossed,he's keen to be converted!
Thanks

---

### Post by Aearenda on 2009-11-26
This should do the trick: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Elfy on 2009-11-26
They are stored in /var/cache/apt/archives

You could just copy them to your friends folder and then do sudo apt-get update.

Alternatively try using aptoncd, it's in the repos - install on your machine, get the updates. Have him install it on his and send him the cd's as you need to.

---

### Post by MisFitt on 2009-11-26
Thankyou,absolutely perfect.
Hopefully I get it right!

---

### Post by MisFitt on 2009-11-26
Thankyou very much,it appears very good-and so fast!

---

### Post by MelDJ on 2009-11-26
see also [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by MisFitt on 2009-11-26
Thankyou,very helpful!

---

### Post by airtonix on 2009-11-26
**your machine**
1. tweak /etc/apt/sources.list  to your liking
2. sudo apt-get update
3. sudo apt-get install aptoncd
4. sudo apt-get install <insert space delimited list of your desired packages here>
5. sudo apt-get update && sudo apt-get upgrade 
6. run aptoncd, > burn ISO

**remote machine**
1. insert cd created with aptoncd 
2. add it as a repository
3. sudo apt-get update && sudo apt-get upgrade.


***notes***
you will have problems if remote cpu architecture is different to your base machine.

In this case, you're better off approaching this situation with apt-mirror and taking the resulting mirror on a removable hard-drive.

---

