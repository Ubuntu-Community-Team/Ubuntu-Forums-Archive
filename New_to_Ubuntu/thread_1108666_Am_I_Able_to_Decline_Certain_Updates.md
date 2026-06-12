---
title: "Am I Able to Decline Certain Updates?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by mwimmersc on 2009-03-27
Is it possible to decline certain updates on Ubuntu? After a long trial & error effort I found out that I needed to downgrade to the version 1.25-1 of the libdvdcss2 driver in order to play DVDs. But now the system tries to update to 1.29-2 all the time. Under Windows, I used to be able to refuse certain updates. Is that possible under Ubuntu too? Thanks!

I am running 8.04 on an HP Pavillion DV2000.

---

### Post by dfreer on 2009-03-27
You most certainly can; apt-pinning I believe is the answer you are looking for. Basically you just tell the package manager that you do not wish to upgrade that package and it will ignore it.

EDIT: This might help:
[http://www.linuxquestions.org/questions/debian-26/prevent-apt-get-from-upgrading-a-package-449984/](http://www.linuxquestions.org/questions/debian-26/prevent-apt-get-from-upgrading-a-package-449984/)

---

### Post by mwimmersc on 2009-03-27
Thanks for your quick reply, dfreer. How do I apt-pin? Sorry, I'm really an absolute beginner :-)

---

### Post by mwimmersc on 2009-03-27
Thanks for the link, I locked the version under synaptic>package. How do I mark this thread as solved?

---

### Post by dfreer on 2009-03-28
> **mwimmersc said:**
> Thanks for the link, I locked the version under synaptic>package. How do I mark this thread as solved?

I believe you advance edit your original post and just add a [SOLVED] to the beginning; for some reason I thought there was a button you could click too that marked it as solved.

FURTHER EDITING: [http://ubuntuforums.org/showpost.php?p=6942769&postcount=9](http://ubuntuforums.org/showpost.php?p=6942769&postcount=9)

---

### Post by kaibob on 2009-03-28
> **mwimmersc said:**
> How do I mark this thread as solved?

Go to your original post, edit the title (go advanced button), and add [SOLVED] or whatever you want.

---

### Post by mwimmersc on 2009-03-28
Cool! Advance Edit was the information I needed.

---

