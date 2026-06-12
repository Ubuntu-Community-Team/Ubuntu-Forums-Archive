---
title: "synaptic package quick search greyed out"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by 007casper on 2010-07-07
I have updated from 9.04 to 10.4.  After upgrade, I went to synaptic and the quick search box is greyed out.  I cant seem to make it work.  Please, advise.  Thank you.

---

### Post by SKhan on 2010-07-07
i am new linux user. have been using it for only about 2 months. until somebody solves your issue, you may use "ubuntu software center" instead. It's at the bottom of application menu.

---

### Post by Peter09 on 2010-07-07
Just a quick sanity check
 
[LIST=1]
[*] You need to run synaptic with 'sudo' to get very far although I am not sure wether that affects the search bar.
[*]Check on the tabs down the side of the window (not really tabs, but selections). Make sure you have not filtered everything out.
[/LIST]

---

### Post by philinux on 2010-07-07
> **007casper said:**
> I have updated from 9.04 to 10.4.  After upgrade, I went to synaptic and the quick search box is greyed out.  I cant seem to make it work.  Please, advise.  Thank you.

To get round this just left click any app to highlight it and then type. This is what the quick search does.

Open a terminal and update the system.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any error messages if any.

---

### Post by 007casper on 2010-07-09
I did do 
sudo apt-get update && sudo apt-get upgrade

quick search still doesnt work.  However, the magnifying glass is clickable and I get a pop box and it works that way.

Does anyone know how I can fix this issue?  I am just worried that there is something missing in the system/kernel

---

### Post by Chris1274 on 2010-07-09
That happened to me on a previous install too. I used the search function under the edit tab and it worked, so you may give that a try.

---

### Post by 007casper on 2010-07-11
yeah, that works... thank you.

still wondering if there is something wrong with the system, and scratching my head thinking what else is wrong that I am not aware of...  How can I figure that out?

when I do update I figure it will fix corrupted/failed files? I guess it doesnt

any suggestions... thank you.

---

### Post by brujoquizz on 2010-07-11
Maybe reinstalling synaptic may work...

In a terminal type:
```
sudo aptitude reinstall synaptic
```

---

