---
title: "Find hardware and drivers"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by crew51m on 2009-05-06
How do I find what hardware I have? Like the manager in windows that show what hardware is on the system.

---

### Post by zeroseven0183 on 2009-05-06
Run **System Testing** in **System > Administration**. After the tests, you have option to display the results on a XML file by clicking the link **View Reports**.

The result is kind of technical though.

---

### Post by 3rdalbum on 2009-05-06
These two commands:

```
lspci
```
```
lsusb
```

---

### Post by anti_microsoft on 2009-05-06
Or lshw, little more detailed then lspci.

---

### Post by freeman2000 on 2009-05-07
Go to  Applications -->  System Tools -->  Device Manager.  The left pane will show a listing of all your hardware.  Click on any item and the right panel will give you in-depth information on that item.

---

### Post by crew51m on 2009-05-07
Thanks. I couldnt find it so I installed it. It is pretty good it shows "everything" that is or on in the laptop.

---

