---
title: "flash issue?"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by refeek on 2011-04-01
So I just installed Ubuntu 10.10 a couple days ago, and as I've been settling in, my massive concentration required me to gain sustenance.  I went to the Papa John's website, and when I went to the "create a pizza" area, things just kind of disappeared as I scrolled over them - now, I could still click the area and add things, and it would refresh and show it properly, but then I would scroll over again and it did the same thing.  The pictures disappeared, and the center area would go white (where it would announce the topping, I presume).  The same thing happened on the Dominos site as well.

I downloaded Flash Aid, and tried manually installing Flash Player 10.2 via terminal.  So I'm not sure if it's an issue there, or maybe with my theme -- is that even possible?  Any help would be nice, since I'm not really sure if it would happen with any other sites.

---

### Post by wolfen69 on 2011-04-01
Does it happen in any other browser like Chromium? That would tell us a lot.

---

### Post by xXNI4NI on 2011-04-02
Mildly unrelated but sounds like the same troubles I read regarding full screen flash controls. Have you given ```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```
a shot?

---

