---
title: "Uninstalling packages / apps"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Solarium on 2009-01-02
Well i am a new comer from Win XP, so far the transition has been smooth haven't turned my desktop pc with windows for 2 weeks now ... so fair to say its going good :D

I don't have any problem in particular but its rather a more general knowledge question (Tryed googling for it but get some odd results):

I would like to know how the uninstall process of packages / apps works in ubuntu.
In windows you have the uninstall button or in worst case u can use the regedit and then delete the files from HD, simple enought.
But when i am installing apps i see that it downloads like 7 packages and installs them, when i remove it i trust the "Add/Remove" completely that its doing its job.. and if it doesn't there is nothing i can do since the packages names are less then logical (to me) and i got no clue where they are installed and what files depend on them.

So if one of you good people could post a nice guide or even a little explanation about the whole process would be greatly appreciated and will definitely boost my confidence level in the installing and uninstalling apps.

---

### Post by wmoore on 2009-01-02
You remove packages either through Synaptic or with ```
sudo apt-get remove <package>
```

As I understand it, when you remove a package dependancies will be removed too, unless you have other packages installed which also depend on them. There is also a command to remove all 'unused' packages but I've never used it so don't know if it behaves itself.```
sudo apt-get autoremove
```

---

### Post by Goll on 2009-01-02
Or go to Add/Remove applications.
Or Synaptic, under Administration

---

### Post by stoogiebuncho on 2009-01-02
If you're worried about having packages around that are no longer used by any of your programs, the easiest way to get rid of them is to open up a terminal and type 
```
sudo apt-get autoremove
```

The apt-get system is one of the first things I fell in love with when I began learning Ubuntu.  It's so well-organized and easy.

edit* --oops, somehow I missed that wmoore had already posted this.

---

### Post by chrisod on 2009-01-02
If you install something manually outside of apt-get, simply deleting the programs folder (and the hidden config folder) is all that is usually needed to delete the program.

---

### Post by donkyhotay on 2009-01-02
As mentioned previously doing the occasional 
```
sudo apt-get autoremove
```
will take out anything that might have been missed when uninstalling (though this is pretty rare). Another good command similar to it is 
```
sudo apt-get autoclean
```
which takes out the package files themselves. Once in a very rare while you'll run into something where you'll get something thats *still* floating around in there at which point you just use deborphan (I use gtkorphan for the GUI interface) to pull it out. Generally though these options aren't needed that often as the standard 'apt-get remove' does a pretty good job.

---

