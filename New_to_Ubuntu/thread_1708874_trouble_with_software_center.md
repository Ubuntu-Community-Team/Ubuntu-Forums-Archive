---
title: "trouble with software center"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by jklap on 2011-03-17
Hello! I Switched to ubuntu 10.10 from windows 7 and I love it! 

I'm trying to download software from the software center but there isn't the option to install. It just says its available from universal source and theres an option to update now. I click it and nothing happens, what gives?

---

### Post by cap10Ibraim on 2011-03-17
type in the terminal 
```

sudo apt-get update 

```
and then visit again the software center

---

### Post by jklap on 2011-03-17
Ok I did that and it still doens't give me the option to actually download anything just update now.

---

### Post by jmszr on 2011-03-17
jklap,

Just a thought, Go to System > Administration > Software Sources > Ubuntu Software and make sure the first four checkboxes are checkmarked (main, universe, restricted, and multiverse).
If any aren't, of course, then checkmark them.
 
It should then ask you to update, if not, then:

```
sudo apt-get update
```

and: 
```
sudo apt-get upgrade
```

Now try the Software Center again.

Hope that helps.

---

### Post by jklap on 2011-03-17
Ok I did all that, all the boxes are checked, but I still have NO option to install

---

### Post by cap10Ibraim on 2011-03-17
try installing from synaptic package manager and report back

---

### Post by jklap on 2011-03-17
I looked up software center in synaptic and its listed as installed. Should I re-install it?

---

### Post by cap10Ibraim on 2011-03-17
no I mean can you install any application (all those in the software center are listed in the package manager too) from the package manager ?!

---

### Post by jklap on 2011-03-17
That seemed to work. Thanks for the help!

---

