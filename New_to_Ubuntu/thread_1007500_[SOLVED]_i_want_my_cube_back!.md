---
title: "[SOLVED] i want my cube back!"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-12-10
hi there!
ok, im on ibex now and it looks great, no argue about that.
thing is that i cant find the way to have my cube back.

i mean, i used to have 4 desktops in gutsy, but now i only have 2 and no effects at all!

so, please, tell me how to set it up.
thanks!

---

### Post by Het Irv on 2008-12-10
```
sudo apt-get install compizconfig-settings-manager
```

that will install the program that you can use to configure the Cube and other effects.

---

### Post by jsf_pp on 2008-12-10
> **Het Irv said:**
> ```
sudo apt-get install ccsm
```

that will install the program that you can use to configure the Cube and other effects.

damn!

```
julio@Chulio-lappie:~$ sudo apt-get install ccsm
[sudo] password for julio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm
julio@Chulio-lappie:~$ 

```

what should i do now?

---

### Post by Het Irv on 2008-12-10
Check for CCSM in Add/Remove... it should be there.

---

### Post by Sealbhach on 2008-12-10
```
sudo apt-get install compizconfig-settings-manager
```

That should do it.


.

---

### Post by philinux on 2008-12-10
Then you want General Options>Desktop Size>Horizontal to 4

---

### Post by jsf_pp on 2008-12-10
> **Het Irv said:**
> Check for CCSM in Add/Remove... it should be there.

thank you!
now i'll be showin off my ibex effects to everybody!
MWAHAHAHAH

cheers!

---

### Post by Keen101 on 2008-12-10
well, it looks like you figured it out.


> sudo apt-get install compizconfig-settings-manager

I don't know what the other one does, but this gives you options to change practically every compiz-fusion setting and plugin. It installs a shortcut on the >Prefrences menu.

---

### Post by Het Irv on 2008-12-10
the other one.... is a typo... I forgot that you had to spell it out in apt-get

---

### Post by Sealbhach on 2008-12-10
You can also install

```
sudo apt-get install simple-ccsm
```

which allows you to enable cool opening/closing effects.


.

---

