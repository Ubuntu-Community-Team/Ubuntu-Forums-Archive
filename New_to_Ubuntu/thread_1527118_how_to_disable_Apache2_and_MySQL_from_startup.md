---
title: "how to disable Apache2 and MySQL from startup?"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-07-08
I installed these along with drupal because I was planning on hosting my own website, but now they start up at boot, and I just put them on there to see how they work when I get around to it (I haven't found a way to actually use drupal yet, no gui interface :confused: ) Although now they suck up RAM for doing nothing, how would I stop them?

---

### Post by stmiller on 2010-07-08
```
sudo apt-get install bum
```

The run the Boot Up Manager located in System > Administration > Boot Up Manager

That will let you turn on or off services.

---

### Post by Legendary_Bibo on 2010-07-08
> **stmiller said:**
> ```
sudo apt-get install bum
```The run the Boot Up Manager located in System > Administration > Boot Up Manager

That will let you turn on or off services.

Cool! I have a question though, it showed that mysql was already deactivated among other things that are usually on. Did it by change change anything? Or does it just show what's on as is at the moment I started it up? Should I be worried?

---

