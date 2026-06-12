---
title: "Xsession unable to launch &quot;Lubuntu&quot; X session ---&quot;Lubuntu&quot; not found; falling back to"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-06-19
I get this error when I login Xsession unable to launch "Lubuntu" X session ---"Lubuntu" not found; falling back to default session

press ok then everything works fin how do i fix

---

### Post by jtarin on 2011-06-19
What version of Lubuntu are you using?

---

### Post by jtarin on 2011-06-19
[Found this.]("https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/660260")
> It would appear the common factor is reusing a previous /home folder? Is there any information we can give to help out with this? I have reopened the bug by marking it as confirmed now that it can be reproduced.

---

### Post by jrd261 on 2011-10-28
This seems like a known bug. Try removing .dmrc from your home directory and rebooting. In other words...

```

rm ~/.dmrc

```

---

### Post by papu40000 on 2012-01-26
jrd261 thank you!
It works for me!!

I was trying autologin for Lubuntu, but this error deviates to LXDE login... three hours to "understand" and focus in this direction/problem: "the xsession problem with xubuntu"

now I can go to sleep happy :D

---

### Post by LorraineO on 2012-03-16
I had the same problem crop up and this worked for me. I had done a re-install but kept my Folder. :p

---

