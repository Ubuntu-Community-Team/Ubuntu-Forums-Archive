---
title: "moving folders - permission denied"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by fabjoa on 2009-12-03
Hey

I'm trying to move a folder from Desktop to home by dragging it using the mouse and it says "Permission denied". I tried with sudo cp and get 'omitting directory' message. My question: how can I move folders with the mouse from one location to another?

Kind regards

---

### Post by ukripper on 2009-12-03
> **fabjoa said:**
> Hey

I'm trying to move a folder from Desktop to home by dragging it using the mouse and it says "Permission denied". I tried with sudo cp and get 'omitting directory' message. My question: how can I move folders with the mouse from one location to another?

Kind regards

if files are there in folder you will need -R switch with cp like below:
```
sudo cp -R /folder /Newplace/
```

hopw it helps. for moving folder you should use mv not cp
```
sudo mv /folder /Newplace/
```
this will move your folder with all files in it

with mouse you need correct permssions to move. By the way, which folder you are trying to move and where?

---

### Post by endBc on 2009-12-03
Probably some of the files inside the given directory aren't owned by you.

```
sudo cp -r source/* target/
```
```
sudo mv source target
```

---

### Post by wojox on 2009-12-03
```
gksudo nautilus
```

Be careful.

---

