---
title: "Error when trying to select &quot;Extra&quot; for Visual Effects"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Xan09 on 2010-11-22
Everytime I try and select Extra or even Normal i get a message saying "The Composite extension is not available" I am using 10.10. What do I have to do to fix this?

---

### Post by cariboo on 2010-11-22
What graphics card do you have, and what drivers are you using?

---

### Post by Xan09 on 2010-11-23
It's an Nvidia GeForce GTS 250, as for the drivers Ubuntu installed it itself when i first booted it up it prompted me to install a proper driver for the card and i did, where can i check which exact driver it is?

---

### Post by TroyDowling on 2010-11-24
System > Administration > Additional Drivers.

You can also get a quick overview by punching this command into the terminal (Applications > Accessories > Terminal):

```

glxinfo | head -n 5

```

---

### Post by Xan09 on 2011-01-03
It told me i have the latest and correct driver  when I selected "Additional Drivers" 
This is what i got after i placed that code into the terminal. Also sorry for the long wait, I had finals and then holiday stuff. Thank you for bearing with me.


name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

---

