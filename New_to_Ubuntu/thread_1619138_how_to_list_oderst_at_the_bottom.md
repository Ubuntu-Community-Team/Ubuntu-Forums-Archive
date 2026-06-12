---
title: "how to list oderst at the bottom?"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by joesto1 on 2010-11-11
hi all
i have ubuntu 10.04 and when i list a log file with gnome (i think)
it shows the contents of the log with the latest at the bottom of the listing, 
how do i set it up to display the lastest entry ay the top for example

this one at 20pm
this one at 21pm
this one at 22pm
etc

i would like it to display like this
this one at 22pm
this one at 21pm
this one at 20pm
etc

as you can see if the log is very log then i have to scroll down the get the latest input
any ideas please
thanks
joe
:P

---

### Post by bioterror on 2010-11-11
```

sudo less /var/log/auth.log

```
enter your password, press end -button and scroll up with pgup button.

---

### Post by Hippytaff on 2010-11-12
you could also 
```

tac /var/log/aith.log

```

---

