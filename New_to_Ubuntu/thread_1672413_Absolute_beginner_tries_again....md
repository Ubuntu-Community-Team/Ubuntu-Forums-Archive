---
title: "Absolute beginner tries again..."
date: 2011-01-20
forum: New to Ubuntu
---

### Post by morgandy on 2011-01-20
My last post seems to be both double-posted and empty, so, I'm really sorry but I don't  know what happened, and here goes another try...  Also, maybe this post  should be in the security thread instead, but since I'm a newbie I  thought I might get a more comprehensible (to me) answer here.

I  am new to Linux and Ubuntu, and barely even moderately computer-savvy at  best, so be kind... Last week I had my first-ever run-in with a  malicious website.  I clicked on an image using google image search, it  redirected me to a fake security website, and then it immediately  started downloading an .exe file (Sorry, I didn't think to get the url  at the time).  I wasn't able to force quit Firefox, and the file  downloaded itself--rapidly--onto my computer, and that was that.  As far  as I can tell it didn't actually run.  I haven't used the machine very  much since it happened, but as far as I can tell nothing is different.  I  have since started using NoScript, which various support threads have  suggested will stop it from happening again, but I am left with these  questions.

I assume this file is somewhere on my computer now (Ubuntu 10.04).  How can I find it and delete it?

If  it's not possible to find and delete it, is it at all safe to assume  that, since it probably only targets Windows, it's safe to continue  using the machine as it is?

If it's not safe, are there any alternatives to reinstalling the OS?

Also, is there anything instead of/ in addition to the NoScript add-on that I should consider for internet security?  

Thanks in advance for your help.

---

### Post by mikewhatever on 2011-01-20
Can you elaborate a bit on the part of "and then it immediately started downloading an .exe file". What happened exactly?
Just to reassure you, exes don't run on Ubuntu, so that you are in no danger.

---

### Post by Bucky Ball on 2011-01-20
Welcome.

To find, open a terminal (Applications>Accessories>Terminal) and paste this:

```
locate .exe
```

.exe files will not execute in Linux. Bug won't affect you (if it is one) but might be passed onto a Windows machine if you are swapping files or on a network.

---

### Post by rewyllys on 2011-01-20
Click on "Places" at the top of your screen, then on "Search for Files...", and insert ".exe" (without the quotes) as the file(s) that you want searched for.  When you find the ".exe" file with the appropriate time-stamp, just delete it.

---

### Post by 3rdalbum on 2011-01-20
By default, Firefox downloads go to the Downloads folder in your home directory. It shouldn't be necessary to use the 'locate' or 'find' commands because, through permissions control, Firefox literally cannot put files anywhere except your home directory and /tmp.

---

### Post by ubudog on 2011-01-20
> **3rdalbum said:**
> By default, Firefox downloads go to the Downloads folder in your home directory. It shouldn't be necessary to use the 'locate' or 'find' commands because, through permissions control, Firefox literally cannot put files anywhere except your home directory and /tmp.

Still, locate would be useful in this situation.  Also, there is no need to worry about a virus, so you don't have to go lock all your Windows (though recommended) right now, because Ubuntu can't execute .exes.  Still though, it would be nice to remove.

---

