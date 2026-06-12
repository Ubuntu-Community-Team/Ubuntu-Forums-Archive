---
title: "LOST buttons from windows"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by dazndom on 2010-06-23
i been foolin around with AWN and WIDGETS and somehow i have lost my max-min-close buttons from all windows
[IMG]http://file:///home/darren/Desktop/Screenshot.png[/IMG]

this has started since last system update, lastnite i think
Any suggestions

cheers D
[IMG]file:///home/darren/Desktop/Screenshot.png[/IMG][file:///home/darren/Desktop/Screenshot.png](file:///home/darren/Desktop/Screenshot.png)[IMG]file:///home/darren/Desktop/Screenshot.png[/IMG]

---

### Post by Perfect Storm on 2010-06-23
Do;
<alt>+<F2>
```
compiz --replace
```


By the way you can't link stuff like that from your computer. You need to upload it to host/server or UF file attachment.

---

### Post by dazndom on 2010-06-23
TO EASY !!!!  ALL FIXED

thanks for that and being so quick

ciao D

---

### Post by Perfect Storm on 2010-06-23
If it still happens when you boot into Ubuntu;

<alt>+<F2>
```
gconf-editor
```

Desktop ---> Gnome ---> Session ---> required_components

Change 'windowmanager' to **compiz**

---

