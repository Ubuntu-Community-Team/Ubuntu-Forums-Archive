---
title: "Samba and Windoze? can't see shares? Help?"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by jazzman8866 on 2008-01-26
I can't see my linux shares from windoze. when i am in linux, i can see my windoze shares o.k, but the other way around .. . i'm lost. any help for a newbie?

i would like to go ubuntu full time but i need to make sure that it will do all that i need it to.

thanking you all in advance.

puff daddy pastery...!

:mad:

---

### Post by jonandrews on 2008-01-26
Take a look at my step-by-step Ubuntu / Windows networking guide:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by swerdna on 2008-01-26
> **jazzman8866 said:**
> I can't see my linux shares from windoze. when i am in linux, i can see my windoze shares o.k, but the other way around .. . i'm lost. any help for a newbie?

i would like to go ubuntu full time but i need to make sure that it will do all that i need it to.

thanking you all in advance.

puff daddy pastery...!

:mad:
That's usually because of error in either or both of these errors in the paragraph called [global] in the Samba configuration file located at /etc/samba/smb.conf; viz::
1: netbios name not specified like this: **netbios name = whatever**
2: the workgroup name in Ubuntui doesn't match the workgroup name in windows box.

Probably it's item #1.

If continue have difficulty, post your file smb.conf

Swerdna

---

