---
title: "how to install vuze 4.2??"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by enri2 on 2009-06-11
ok i dl'ed  4,2 , extracted it and ran in terminal "./azureus" but that doesn't install it  so it appears on the applications menu... how do I install it?????

---

### Post by halitech on 2009-06-11
is vuze not in synaptic?

---

### Post by enri2 on 2009-06-11
> **halitech said:**
> is vuze not in synaptic?
it is but this is the latest version

---

### Post by lambophil on 2009-06-11
It should just run from the extracted folder I think... Just run the app file - it should say in the README. I run mine from the home folder at the moment it works fine.

---

### Post by michy99 on 2009-06-11
Does it need to be compiled first?

---

### Post by enri2 on 2009-06-11
thanks all, I installed a .deb and it works fine , but it can't update. it says user/share/vuze  is not writable. and vuze keeps keeps starting up by itself

---

### Post by enri2 on 2009-06-11
i fixed my problem by copy/pasting the update files manually. but now ehn i start vuze it says "folder  user/share/vuze is not writable, this will prevent future updates"

---

### Post by zvacet on 2009-06-11
You can get Vuzer from [here.]("http://www.getdeb.net/search.php?keywords=vuze")If you want to be able to update it you can add this line to your source list


```
gksudo gedit /etc/apt/sources.list
```

add  

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Save and close file.

```
sudo apt-get update
```

---

### Post by enri2 on 2009-06-11
ok thanks all, have a nice day.

---

