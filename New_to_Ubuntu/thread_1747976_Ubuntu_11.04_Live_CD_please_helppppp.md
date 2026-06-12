---
title: "Ubuntu 11.04 Live CD please helppppp"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Serry911 on 2011-05-03
hello every body iam using ubuntu 11.04 and i updated to gnome3 then i have the damn error which couldnt log me in ( .ICEauthority error) i tried to solve the error but no success now i downloaded the ubuntu 11.04 cd and what i only want is to copy my home folder to external hard and re install ubuntu but when i try to open my home folder it give me an error that i dont have the permession can anyone tell me what to do pleaseeeee
i will appreciate any idea

---

### Post by Steve H on 2011-05-03
Do you have your Home on a separate partition?

If so, might be worth trying to boot from the CD, and see if you can "Upgrade from 11.04 to 11.04". I screwed up my Unity desktop by installing Gnome3 (didn't like it, too buggy) so to get back to Unity I did the CD boot upgrade and then ran

```
sudo apt-get autoremove
```

Worked for me but I have a Home partition so all the data was safe.

Also when I did a Google search for "Ubuntu .ICEAuthority" [this came up]("http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8-10-a-681312/"). Might also be worth checking out.

Hope that helps.

---

### Post by pme 72 on 2011-05-04
Take a look at this post:

Accessing protected Ubuntu files from Live CD

[http://ubuntuforums.org/showthread.php?t=1745719](http://ubuntuforums.org/showthread.php?t=1745719)

---

