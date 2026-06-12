---
title: "Ubuntu Software Center Help!"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by deming1019 on 2011-02-11
Every time I try to install something in the Software Center it lets me enter my password, but then it tells me 


[CENTER][B]Previous installation hasn't been completed
The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.[/B]
[/CENTER]

Can someone please help me fix this?

---

### Post by trozamon on 2011-02-11
Try opening a terminal and typing: 

```
sudo apt-get -f
```

---

### Post by lhb1142 on 2011-02-11
I have never seen anything like this so I may be grasping at straws but I suggest that you go into the Synaptic Package Manager (under System->Administration) and then, in the lower left column, you will see Custom Filters. Click on that and then you will see, in the upper left hand, several choices.

I would check Broken Packages, Marked Changes, and/or Missing Recommends and see if anything is in there which you could update to correct this situation.

I am by no means a Ubuntu expert but I hope that this suggestion is of some help to you.

Lawrence

---

### Post by Frogs Hair on 2011-02-11
If there are broken packages listed in the synaptic package manager , use the edit tab and select repair broken packages.

---

### Post by odessa2 on 2011-03-30
I have a similar problem but the Synaptic Package manager wont even start.  I get the error


E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Any help would be appreciated!

---

### Post by Frogs Hair on 2011-03-30
Hi and Welcome 

Try this in the terminal  ```
sudo apt-get install --reinstall package name 
``` insert package name after reinstall with a space between .

---

