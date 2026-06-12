---
title: "Added Amarok 2.0-Need to remove all dependincies as well"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by grewolf on 2009-02-22
I wanted to try out Amarok 2.0.  I went on the web and found what I needed on the forum here

[HTML]http://ubuntuforums.org/showthread.php?t=1008157&page=3[/HTML]

I was using Amarok 2.0 and it seemed to be working ok but then I went to play a game that changed my resolution and everything went wonky(Resolution needed restart to change KDE Icons etc.).  I went to Synaptic and clicked on completely remove amarok thinking that would solve my problem.  Unfortunately it left some of the dependencies from amarok 2.  Is there a way I can remove them with the command line quickly or do I have to go through synaptic look at all the dependencies and remove them one at a time cross referencing to make sure I don't remove something that another package I want relies on it.

---

### Post by oldos2er on 2009-02-22
```
sudo apt-get autoremove
```

---

