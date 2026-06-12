---
title: "Need Help with Update Manager"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by LoganS on 2010-03-12
I am running Ubuntu 9.04.  I am having a problem with Update Manager not working. The error message involves a missing version of polkit-grant2. I have searched this site and the internet but I can not find a solution. Does anyone have any information about this and how I might deal with the problem?

Thanks

---

### Post by akand074 on 2010-03-12
I'm not sure if this is going to work but go to Accessories > Terminal and copy paste this in:

```
sudo apt-get install gksu-polkit
```

---

### Post by LoganS on 2010-03-12
Thanks for the suggestion. I tried it and got the error message of[B] E: Couldn't find package gksu-polkit
[/B]
 I looked on internet but could not determine which gksu-polkit would be suitable.

---

