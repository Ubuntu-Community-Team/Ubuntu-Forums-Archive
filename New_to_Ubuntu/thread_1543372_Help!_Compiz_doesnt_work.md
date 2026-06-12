---
title: "Help! Compiz doesnt work"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by justin43384 on 2010-08-01
after plugging in a second monitor into my HP running Ubuntu 10.04, disabled Compositing.  Now compiz settings manager doesnt work.  
Help please
and thanks in advance.

---

### Post by j7%&lt;RmUg on 2010-08-01
urh, could you provide some more information?

Did you just disable compiz, or did you remove it? what graphics card do you have? etc.

You cant expect us to be like magical genies that just solve all your problems straight away.

EDIT: i would remove you email address from your name there, search engine spiders to crawl these forums, you will most likely just get a lot of spam.

---

### Post by justin43384 on 2010-08-02
nisshh I have a Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)Graphics Card
the sequence of events to Compiz Settings manager to stop working was:
1. plug in second monitor
2. when plugged in, Compositing was disabled and is needed for Docky to work
3. I ran the code: gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true
4. Now compiz manager wont work due to compositing

and nisshh i requested a name change already

---

### Post by Legendary_Bibo on 2010-08-02
What type of cable did you use? Have you tried reloading Compiz?

```

compiz --replace

```

---

### Post by theozzlives on 2010-08-02
Are you using the same card for both monitors?

---

### Post by justin43384 on 2010-08-02
Im using a DVI-D Dual Link cable for both monitors

Reloading compiz didnt fix the problem

apparently, with one monitor everything works fine

---

