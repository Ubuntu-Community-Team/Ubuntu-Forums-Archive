---
title: "wifi connection"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by sampath kumar ms on 2010-10-08
hello sir,

 Recently I installed the ubuntu 10.04 to ma laptop.I wanna to connect wifi to it.. How could it possible.. I searched in many site and saw vedios but i didnt get proper information.. Ma laptop needs any drivers for ubuntu to connect wifi.. plz resolve ma problem as soon as possible.. waitin for ur reply..:

---

### Post by Hippytaff on 2010-10-08
Search the posts, there are loads with wifi stuff on...you need to know your chipset to find out which driver you need and search any issues.
 
press Ctrl+Alt+T to open a terminal and enter
 
```

lsusb

```
 
This should give you your chipset and therefore driver info
 
try
 
```

lshw -c network

```
 
to get extra network info.

---

### Post by lotharmat on 2010-10-08
Hiya,

Please can you post the output of 

```
lspci
```

and

```
lsusb
```

This will help to identify what wifi card you have.

Cheers,

---

### Post by Quackers on 2010-10-08
Welcome to UbuntuForums :-)
Do you have an icon in the top right of your screen like the one in the picture? If you do click on it and see if any wifi connections are available.

---

