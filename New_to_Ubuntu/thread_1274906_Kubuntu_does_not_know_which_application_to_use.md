---
title: "Kubuntu does not know which application to use"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by foska on 2009-09-25
Hello all,

Since I installed kUbuntu, I have found that when I download certain files it does not seem to know which application to use to open them and I get a dialog box (see attached screen shot) which asks which application to use to perform the function requested. This also happens when using the "Open Containing Folder" function.

I have tried many times to resolve this issue on my own but I have not been successful. Does anyone know how I can resolve it?

---

### Post by Marflus on 2009-09-25
What file extensions are causing this? I assume most basic files (images, for example) open fine?

---

### Post by kay-man on 2009-09-25
I think the problem is not Kubuntu, but firefox. Try this:

[http://www.google.nl/search?q=linux+firefox+open+containing+folder]("http://www.google.nl/search?q=linux+firefox+open+containing+folder")

You'll need to tweak some firefox settings, but then it should work.

Paul

---

### Post by Ms_Angel_D on 2009-09-25
You can choose which program you want to use to open the file. Click choose and look in /usr/bin for the program you want to use. If you want to browse with dolphin, you have to set the file type "file" to be associated with dolphin in firefox 

```
edit->prefrences->applications
```

sometimes the file type "file" doesn't appear but if you right click on a download and click "open containing folder it should give you the option to choose a program then you can set it to 

```
/usr/bin/dolphin
```
Hope this info helps.

---

