---
title: "SMEM won't Run in 10.04"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Greymatter on 2010-04-30
I installed secure delete but when I tried to run smem it said that must be installed. Is SMEM different in 10.04??

---

### Post by Jon Monreal on 2010-04-30
I doubt it as it's [listed as a package]("http://packages.ubuntu.com/hu/lucid/smem").

Perhaps you should just sudo apt-get install smem and see if it works.

---

### Post by Greymatter on 2010-04-30
I installed smem but it has nothing to do with SMEM from Secure Delete, at least not as it looks to me. I ran it and it showed a list with 

PID User     Command                         Swap      USS      PSS      RSS 

It then has a list of items beneath each. That doesn't appear to have anything to do with Secure Delete functions. How do I uninstall smem now?

---

### Post by Jon Monreal on 2010-04-30
```
apt-get remove --purge smem
```

Maybe you could
```
sudo apt-get install --reinstall secure-delete
```
to reinstall Secure Delete, but I don't know if that will help

---

### Post by Greymatter on 2010-04-30
> **Jon Monreal said:**
> ```
apt-get remove --purge smem
```Maybe you could
```
sudo apt-get install --reinstall secure-delete
```to reinstall Secure Delete, but I don't know if that will help

I did remove it and reinstalled Secure delete. The smem command still won't perform the functions it did with 9.10. Thanks for your help. It's good to learn these things firsthand.

---

### Post by inameiname on 2010-06-04
Did you ever find a solution for this? I'm having the same problem.

---

### Post by drewster1829 on 2010-09-04
The solution is that the command smem in secure-delete has been changed to sdmem.  It's located in /usr/bin/sdmem.  So, to run the secure memory wipe, execute:

```
sudo sdmem
```

For help and options, use:

```
sdmem -h
```

I hope this helps someone. :p

---

### Post by inameiname on 2010-09-04
Awesome Drewster! Thanks. I was curious if this was ever figured out.

---

