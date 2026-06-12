---
title: "[SOLVED] Dependencies"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by theozzlives on 2008-12-03
I have a question, though I think I know the jist of the answer. What is a dependency?/ Sometimes I get a dependency error when installing a *.deb file and I can't install it.

---

### Post by skymera on 2008-12-03
A dependency is something a program needs in order to function.

The dependency error you are getting is probably a file that isn't available through the repositories or needs an older version. 

What program are you trying to install by the way?

---

### Post by theozzlives on 2008-12-03
> **skymera said:**
> A dependency is something a program needs in order to function.

The dependency error you are getting is probably a file that isn't available through the repositories or needs an older version. 

What program are you trying to install by the way?

it just happens now and again, I normally chuck the app

---

### Post by earthpigg on 2008-12-03
is it usually programs you are getting via downloading the .deb from their website instead of through the repos?

---

### Post by theozzlives on 2008-12-03
> **earthpigg said:**
> is it usually programs you are getting via downloading the .deb from their website instead of through the repos?

yeah

---

### Post by earthpigg on 2008-12-03
based on my experience...

#1 best and most reliable way to install software - if its in the ubuntu repos, use that.

#2 - often times they will have ubuntu-specific repos that you can add to your repo list. hopefully, they will also have commonly needed dependancies in their 3rd party repo. i think i was playing around with the most bleeding edge awn and compiz via this method back in 8.04.

#3 - otherwise, they will often have an ubuntu .deb to use. frostwire (FOSS limewire replacement) does this, for example.

#4 - debian .deb. hmmmmm...


edit - i guess teh whole point of this post is that, given a choice between adding to your sources.list to include a custom ubuntu repo for the specific software and downloading a .deb, go for the sources.list.

---

