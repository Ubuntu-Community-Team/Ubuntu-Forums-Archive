---
title: "How to access an Ubuntu share from Windows?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by zirconx on 2007-02-22
My wife runs Ubuntu 6.10, I'm running Windows XP.  She shared out a folder on her desktop, and I'm trying to access it.  No matter what I do on my machine, I just keep getting prompted for a password.  I've even tried her own username/password, no matter what I do I can't access it.  Is there some trick?  I've looked in the smb.conf file, and the share is listed there.

---

### Post by gradedcheese on 2007-02-22
Here's the solution: [http://andrey.thedotcommune.com/samba.html](http://andrey.thedotcommune.com/samba.html)

Basically, do the smbpasswd step that I mention ('Configuring Samba Users'), then restart samba.

---

### Post by zirconx on 2007-02-22
Worked perfect, thanks for the fast response.

---

### Post by gubemton on 2007-11-29
That link is dead.  Can someone provide the new location of that documentation?  Is that info not in the Ubuntu Help function?

---

### Post by sternkanz on 2007-12-04
bumpity, can we get new link? thanks!

---

### Post by rickyjones on 2007-12-04
> **sternkanz said:**
> bumpity, can we get new link? thanks!

I don't have a link but if memory serves just run the following command:

```
smbpasswd -a username
```

---

### Post by jonandrews on 2007-12-04
I've put a step-by-step illustrated guide to Windows / Ubuntu networking on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Have a look & see if it helps

---

### Post by jazzmike on 2007-12-04
> **jonandrews said:**
> I've put a step-by-step illustrated guide to Windows / Ubuntu networking on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Have a look & see if it helps

Thanks,

Worked for me. I've been trying every solution that didn't require the use of Terminal. I like so many other Windows users it seems, was avoiding it like the plague. I also installed Java6 using Terminal with major success.

jazzmike

---

### Post by strBean on 2008-03-09
Hey, jonandrews, thanks!  Very succinctly worded so it came up in my Google search right at the top, took care of the mystery for me...

---

### Post by Dragonflyoh on 2008-03-09
Thanks for the information. Worked as advertised.

---

