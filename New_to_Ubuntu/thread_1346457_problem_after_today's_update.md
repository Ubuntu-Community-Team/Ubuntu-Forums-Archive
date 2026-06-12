---
title: "problem after today's update"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by interceptorV8 on 2009-12-05
after updating, i restarted the computer and after grub loads the latest kernel, i get a black login screen displaying similar text seen in the terminal asking me to login

i'll type in my user name and then password... it'll do some stuff and presumably finish loading... and then it will take me to the main ubuntu 9.10 login screen where i have to login AGAIN.  

what happened?

---

### Post by Paqman on 2009-12-05
> **interceptorV8 said:**
> 
what happened?

For some reason your X server isn't starting. Log in see what happens when you enter:
```
startx
```

---

