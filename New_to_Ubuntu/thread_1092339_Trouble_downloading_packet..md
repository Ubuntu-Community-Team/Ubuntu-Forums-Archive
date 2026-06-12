---
title: "Trouble downloading packet."
date: 2009-03-10
forum: New to Ubuntu
---

### Post by rgb96 on 2009-03-10
Hey guys and gals,

I'm writing a program in perl on my machine, and I need a certain packet (Math::Pari 2.001804 at least to be specific,) but when I download the most current version, I run in to trouble. After I un-tar it, the directory is listed as locked and unreadable. I can't cd into it or anything. I thought maybe it was just a bad download, so I tried deleting it and re-downloading 3 times, but got the same result every time. Any ideas why this is happening?

P.S. I tried downloading older versions, but when I run the Makefile.PL, the packet tries to download additional files, and the downloads always time out, so I can't make the rest of the build.

---

### Post by taurus on 2009-03-10
Where did you unpack it and who is the owner of that new directory?

You probably just have to change the ownership back to you so you can write to that new directory.

---

### Post by rgb96 on 2009-03-10
I just unpacked into my home directory. How do I change ownership to me? 

sudo chown $username $directory  ?

---

### Post by taurus on 2009-03-10
Did you unpack it in ~/Desktop?

```
ls -la ~/Desktop
```
If you want to change the ownership of that new directory, you would something like

```
sudo chown -R username:username /path_to_that_new_directory
```
Replace username with your login name.

---

### Post by rgb96 on 2009-03-10
Thanks. Changing the owner to myself got me into it.

Now I'll just cross my fingers and hope this version wll actually install. haha

---

