---
title: "HELP: I found a rootkit and a few other potential problems"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by YosefKaro on 2010-06-08
Using chkrootkit, I found that I have an infection.  Additional, I may have a few other problems.  Here is the pastebin of the output from chkrootkit: [http://pastebin.com/Qbzvggqs](http://pastebin.com/Qbzvggqs)

I welcome all of your advise.  Thanks.

-Yos

---

### Post by iponeverything on 2010-06-08
Just nuke your install and start over. The cause of many cases like your has been the use of weak passwords that could be brute forced.

---

### Post by YosefKaro on 2010-06-08
I'd really rather not 'nuke' my current install; at this point, it would cause a lot of headaches.  Instead, how can I change my password to a much stronger one?  

Anyone else have any other advise?

-Yos

---

### Post by bhuvi on 2010-06-08
its better to backup your documents and do a clean install from the beginning,because it is difficult to remove all the changes introduced by the rootkit and remember to check your executable programs for any modifications.

---

### Post by sydbat on 2010-06-08
Have you run rkhunter? If not, you should. 

I find that both rkhunter and chkrootkit show some false positives.

Also, I notice you put wubi as your install (in the thread title). I wonder if that might have more to do with it than an actual rootkit. Personally, I would back everything up and install Ubuntu into it's own partition. Far less problems that way.

---

