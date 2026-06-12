---
title: "'gDesklets' Error"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by chome4 on 2009-06-29
Installed 'gDesklets' following instructions, but when I attempt to launch the icon in Applications, it get:


Failed to execute child process "gdesklets" (No such file or directory)

How do I point the icon to the correct directory?

---

### Post by Sukotto on 2009-07-04
I am getting the same error.

I ran ```
sudo aptitude install gdesklets gdesklets-data 
``` in the terminal then went to Applications --> Accessories --> gDesklets

then that error comes up.

any ideas?

Thanks, Scott!

---

### Post by sdlynx on 2009-07-04
I also get this...

---

### Post by sdlynx on 2009-07-04
I seemed to have fixed the error by installing python2.5 ```
sudo apt-get install python2.5
```

---

### Post by Sukotto on 2009-07-04
Cool, That fixed it!

---

### Post by chome4 on 2009-07-21
Fixed it for me, too!

Thanks.

---

