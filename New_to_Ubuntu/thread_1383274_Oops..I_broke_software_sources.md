---
title: "Oops..I broke software sources"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-17
I was trying to add Wine to software sources and screwed up (again!). I am getting this error message now

E: malformed line 55 in source list/etc/apt/Sources.list (dist parse)
E: unable to lock the list directory

go to repository dialogue to correct the problem

E:_cache-> open() failed, please report

Help?  :)

---

### Post by 3rdalbum on 2010-01-17
> **ThePinkWitch said:**
> E: malformed line 55 in source list/etc/apt/Sources.list (dist parse)

The 55th line of the file '/etc/apt/sources.list' is wrong. Either change it so that it's correct, or disable the line by putting a # symbol at the beginning of the lines. All lines in this file must begin with 'deb', 'deb-src' or the #.

> go to repository dialogue to correct the problem

Might also work as well. The "repository dialog" is System > Administration > Software Sources. You should ALWAYS add repositories using this program rather than manually editing /etc/apt/sources.list, because it won't let you add any malformed lines to the sources.list.

---

### Post by ThePinkWitch on 2010-01-17
"The 55th line of the file '/etc/apt/sources.list' is wrong. Either change it so that it's correct, or disable the line by putting a # symbol at the beginning of the lines. All lines in this file must begin with 'deb', 'deb-src' or the #."

I have no idea how to change it or where I change it.

I was in Software Sources and was adding Wine the way I was told to on the wine webpage. I must have typed it in wrong or something. My typing sux and there's a lot of it for Ubuntu.

Thanks for your reply.

---

### Post by dnairb on 2010-01-17
In terminal:

```
gksudo gedit /etc/apt/sources.list
```

Enter your password, and check the ouput in gedit.
Edit the file, save and then try again.

To have gedit show line numbers:

Edit > Preferences > tick "Display line numbers"

If you can't see the error, copy and paste the /etc/apt/sources.list output here.

---

### Post by Elfy on 2010-01-17
> **ThePinkWitch said:**
> ... My typing sux and there's a lot of it for Ubuntu...

Try copy and paste then - you don't usually need to do anything other than highlight what needs copying and then click the middle mouse button where you want it pasted.

---

### Post by ThePinkWitch on 2010-01-17
> **dnairb said:**
> In terminal:

```
gksudo gedit /etc/apt/sources.list
```

Enter your password, and check the ouput in gedit.
Edit the file, save and then try again.

To have gedit show line numbers:

Edit > Preferences > tick "Display line numbers"

If you can't see the error, copy and paste the /etc/apt/sources.list output here.
All fixed now.. I missed a space.  Thankyou :)

---

