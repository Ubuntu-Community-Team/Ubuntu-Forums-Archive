---
title: "Mythbuntu crashes"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by davesperry on 2009-07-29
Hi, I'm a noob. I installed ubuntu so I could have a DVR. I installed mythbuntu and I think the install didn't work all the way. Anyway, I restarted my computer and now whenever I try to start mythbuntu a box tries to start and then the desktop freezes, except for the bar on top and bottom with my mouse. I think I need to uninstall and reinstall, but I don't know how to uninstall and if I just try to reinstall it says it is already installed. What can I do?
 
My computer is new and fast.
 
Thanks in advance!

---

### Post by nhasian on 2009-07-29
what version of ubuntu are you using?  you can remove mythbuntu with the command:

```
sudo apt-get remove mythbuntu-desktop
```

did ubuntu work fine before you installed mythbuntu?

you can reinstall the regular desktop with:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by davesperry on 2009-08-12
I'm using Ubuntu 9.04.  Ubuntu worked fine before trying to install the myth program.  It still works fine unless I start the mythtv program.

I tried to uninstall myth by doing this in the terminal:
sudo apt -get remove mythbuntu-desktop

It did some stuff and I was expecting to see the myth front and backend gone, but it is still there....hmmm.. any other ideas?

I'm a super noob

Thanks!

---

