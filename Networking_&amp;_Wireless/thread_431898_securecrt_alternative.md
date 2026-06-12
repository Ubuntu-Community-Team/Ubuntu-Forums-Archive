---
title: "securecrt alternative?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by Bashed on 2007-05-03
I usually use securecrt in windows, it is awesome but wine is not functioning correctly with this (shuts down)

[http://www.vandyke.com/products/securecrt/features.html](http://www.vandyke.com/products/securecrt/features.html)

Any free alternative to this? The default terminal has zero features compared to this and I need to connect via ssh2 with wheel group user THEN su into root.

I need to be able to save profiles, passwords, custom login, custom ports, etc

---

### Post by lcg on 2007-05-03
> **TalkJesus said:**
> I usually use securecrt in windows, it is awesome but wine is not functioning correctly with this (shuts down)

[http://www.vandyke.com/products/securecrt/features.html](http://www.vandyke.com/products/securecrt/features.html)

Any free alternative to this? The default terminal has zero features compared to this and I need to connect via ssh2 with wheel group user THEN su into root.

I need to be able to save profiles, passwords, custom login, custom ports, etc

On Windows, I am using PuTTY for all my SSH needs. It has pretty much everything you describe (I have never used SecureCRT, so I can't really compare them). AFAIK, there is also a Linux version, I don't know how good (or bad) it is, though.

HTH,
Lars

---

### Post by Bashed on 2007-05-03
I'm having a hard time trying to figure out how to install putty in ubuntu feisty fawn

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

I hope someone here can give simplified instructions please

---

### Post by dbott67 on 2007-05-03
It's already in the repositories:
```
sudo apt-get install putty
```-Dave

---

### Post by lcg on 2007-05-04
> **dbott67 said:**
> It's already in the repositories:
```
code sudo apt-get install putty
```

-Dave

Without the word 'code', of course:
```
~$ sudo apt-get install putty
```

Regards,
Lars

---

### Post by dbott67 on 2007-05-04
> **lcg said:**
> Without the word 'code', of course:
```
~$ sudo apt-get install putty
```Regards,
Lars

Oops... sorry about that.  I guess I typed an extra 'code' tag... I'll go back and edit it.

Thanks.

-Dave

---

### Post by Bashed on 2007-05-04
Good grief. Look at the screenshot. What on earth was the putty creator thinking of?

is this normal?

---

### Post by dbott67 on 2007-05-04
I don't know what he was thinking of, but that's what it looks like! :-)

---

### Post by jfinkels on 2007-05-04
> **TalkJesus said:**
> Good grief. Look at the screenshot. What on earth was the putty creator thinking of?

is this normal?

Looks normal to me...what do you mean?

By the way, does everybody know that he/she can just type
```

ssh *username*@*hostname*

```

---

### Post by Bashed on 2007-05-04
> **jfinkels said:**
> Looks normal to me...what do you mean?

By the way, does everybody know that he/she can just type
```

ssh *username*@*hostname*

```

Read my first post.

" I need to be able to save profiles, passwords, custom login, custom ports, etc"

Regarding putty, the problem is the huge, ugly fonts and 1984 comodore interface :)

---

### Post by jfinkels on 2007-05-04
> **TalkJesus said:**
> Read my first post.

" I need to be able to save profiles, passwords, custom login, custom ports, etc"

Woops, my bad. I apologize.

Maybe ssh can do that? Checkout ```
man ssh
``` I assume you can use config files, but I'm not sure if it can do everything you want. I just always go for the traditional/simplest/previously installed program first :D

> 
Regarding putty, the problem is the huge, ugly fonts and 1984 comodore interface :)

Haha yes, that's GTK 1, I believe. I guess they never bothered to update the graphics for GTK2.

Some programs you will encounter will have that ugly GTK1 theme.

EDIT:

You know, it is an open source project...YOU could update it if you wanted to!

---

### Post by Bashed on 2007-05-06
" You know, it is an open source project...YOU could update it if you wanted to!"

Well, not all of us are linux gurus or programmers. Its not my talent or expertise. Otherwise, I'd be updating a lot of things and providing theme here for sure ;)

Ok, so anyone else know of a neat alternative to securecrt AND putty?  Putty looks normal in Windows, so not sure why not in linux.

---

### Post by The Devil Is A Squirrel on 2008-03-25
> **TalkJesus said:**
> " You know, it is an open source project...YOU could update it if you wanted to!"

Well, not all of us are linux gurus or programmers. Its not my talent or expertise. Otherwise, I'd be updating a lot of things and providing theme here for sure ;)

Ok, so anyone else know of a neat alternative to securecrt AND putty?  Putty looks normal in Windows, so not sure why not in linux.

I'd like to know that too.

UPDATE
======
Forget it. I just found out (Duh!) that the terminal is perfectly capable to do ssh connections...

---

