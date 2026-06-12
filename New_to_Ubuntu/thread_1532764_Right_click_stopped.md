---
title: "Right click stopped"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-07-16
Hi Ya'll,
 Okay, just did a fresh download of 10.04 64bit and did a dual boot with a fresh install of Vista. Things were going fine, but..... all of a sudden my rick click in Lucid stopped working! I had posted about this once before while it was in Beta, got no real response, other then a few people saying that they had experienced the same thing. I saw one person said that they had it as an issue with their NVIDIA driver, so I changed mine from one to the other, but no luck. I have not had this problem since it was in Beta, and I am just wondering what is going on and how can I fix my right click. By the way, it works inside applications, just not on the desktop. Any thoughts?
Thanks

---

### Post by wojox on 2010-07-17
Go 

**CTRL + ALT + F1**

Login and run 

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Log out and 

**CTRL + ALT + F7**

---

