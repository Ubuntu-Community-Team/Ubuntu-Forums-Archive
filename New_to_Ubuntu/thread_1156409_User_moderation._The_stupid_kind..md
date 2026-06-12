---
title: "User moderation. The stupid kind."
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Drokles on 2009-05-11
This may sound stupid, but I was wondering what would happen when you take away the privilege of system administration from your own user.

Of course, there's got to be some easy way around it if it goes wrong I thought, but now I can't seem to edit my privileges, and even after learning some command line fu I find that sudo'ing doesn't work either.

Any ideas? :D

~ Drokles

---

### Post by tuxxy on 2009-05-11
You could try system > admin > users & groups.

Unlock with your password and restore your original privileges, you could also try in the terminal with this command;

```
sudo adduser username admin
``` 

Where username is obviously your user :)

---

### Post by anjilslaire on 2009-05-11
reboot into Recovery Mode, where yuo get a terminal prompt as root. Then fix your permissions as needed.

If you need a gui, try ```
startx
```

---

### Post by mprince on 2009-05-11
Here is a link that will guide you:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Drokles on 2009-05-11
Thanks alot, problem fixed!

---

