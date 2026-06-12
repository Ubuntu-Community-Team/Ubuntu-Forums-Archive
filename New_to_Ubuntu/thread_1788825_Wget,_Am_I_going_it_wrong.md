---
title: "Wget, Am I going it wrong?"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by Narchie on 2011-06-23
> wget -r -l12 --accept gif,jpg,jpeg [http://www.websitename.com/page](http://www.websitename.com/page) 

Trying to download images up to 12 levels but it stops after 2 or 3.

Help please?

---

### Post by dcsoldschool53 on 2011-06-23
> **Narchie said:**
> Trying to download images up to 12 levels but it stops after 2 or 3.

Help please?

```
wget -r -l12 --accept gif,jpg,jpeg [http://www.websitename.com/page]("http://atsomewebsite.com")
```As I was looking through the man page for wget to help you with your  problem, I was wondering what is -l12, because, If -l means depth, the  maximum is 5. What you have here says stop after 2 or 3.
Here is the man page for wget command:
[http://manpages.ubuntu.com/manpages/gutsy/man1/wget.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/wget.1.html)

---

### Post by dcsoldschool53 on 2011-06-23
Try it using --no-parent to see if that will help you. There is an example of how to use the no parent option on the man page link.

I hope this will help you.

---

### Post by Narchie on 2011-06-23
I tried noparent, far as I understand it the default is 5 levels but can be changed.

Will keep trying, I am currently using wget -rl8 --accept gif,jpg,jpeg -i /home/user/DL2.txt and creating a list of sub sites to try, seems to be working at least but takes longer to set up.

---

