---
title: "Install webcam?bcus not yet been actve"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Angel gel on 2011-02-17
i cant use my webcam on my Laptop Acer(Aspire 4920)....
pls help to solve this problem...i use ubuntu10.04..

---

### Post by Quackers on 2011-02-17
What kind of webcam is it? 
Try running lspci in a terminal and post the results in code tags.

---

### Post by maqtanim on 2011-02-17
> **Angel gel said:**
> i cant use my webcam on my Laptop Acer(Aspire 4920)....
pls help to solve this problem...i use ubuntu10.04..
Is it a built in webcam?
In which program did you exactly try this webcam? Did you use CHEESE? It is a Photobooth like program. Install Cheese from the software center and run it. Then check out whether your webcam is detected or not.

---

### Post by seawolf167 on 2011-02-17
Like the previous poster says, the easiest thing to do first is install Cheese and see if your webcam is recognized/working

```
sudo apt-get install cheese
```

If your webcam isn't working, then try what Quackers said and post the output of 

```
lspci
```

so we can take a look

---

