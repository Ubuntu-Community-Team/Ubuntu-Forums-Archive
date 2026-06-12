---
title: "I broke my display size and cant get back in"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by mrhobbeys on 2008-12-26
I got a new LCD screen and I could not see all of my desktop so I went in to set it to a different size. I changed it to something like 1380 x 1070 (approx) and promptly got a message "display mode not supported" I have been trying to figure out how to change it back from the terminal but I can not figure it out. Please help

clt+alt+F1-F6 is terminal that I can see. and I am using links right now to post this.

---

### Post by taurus on 2008-12-26
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mrhobbeys on 2008-12-26
Thank you very much!!!!!

Please if you can, how did you learn that?

---

