---
title: "cups is all-powerful?!?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by LintonHanes on 2010-03-09
Hey, what does the printing service (cups) have to do with avidemux, firefox, apturl, etc etc etc

I can't remove cups as it'll cripple the whole OS

nice1"

---

### Post by Psumi on 2010-03-16
Yes, cups is the Common Unix Printing System. Removing it will cripple your system regardless if you have a printer or not.

---

### Post by caravel on 2010-03-16
You should be able to disable the CUPS server from running at startup if that's the issue?

---

### Post by 3rdalbum on 2010-03-16
> **LintonHanes said:**
> Hey, what does the printing service (cups) have to do with avidemux, firefox, apturl, etc etc etc

I can't remove cups as it'll cripple the whole OS

nice1"

Those programs require CUPS in order to print, therefore CUPS is listed as a dependency.

CUPS requires less than a megabyte of RAM at idle... why exactly do you want to remove it? Isn't it okay just to not be configured? It is possible to stop CUPS from loading at startup, but you probably won't notice any difference in startup speed or memory use.

---

### Post by LintonHanes on 2010-03-16
Yeah, shux
it had some large-sh update files and I figured "who needs it" and went to remove it

but resource-wise it's not a bother so what've I got to complain about huh?

---

### Post by sandyd on 2010-03-16
> **LintonHanes said:**
> Yeah, shux
it had some large-sh update files and I figured "who needs it" and went to remove it

but resource-wise it's not a bother so what've I got to complain about huh?
```

sudo mkdir /etc/init.d-disabled
sudo mv /etc/init.d/cups /etc/init.d-disabled/
```

---

### Post by captain.ratsie on 2010-03-25
I was looking to free up disk on a eee don't have a printer on this unit so I thought cups and its updates could  go , but then I noticed ubuntu desktop on the list to go ,,, not good,  step  away from the button

---

### Post by Psumi on 2010-03-25
> **captain.ratsie said:**
> I was looking to free up disk on a eee don't have a printer on this unit so I thought cups and its updates could  go , but then I noticed ubuntu desktop on the list to go ,,, not good,  step  away from the button

ubuntu-desktop is a metapackage. Removing it will not harm your system.

---

### Post by captain.ratsie on 2010-03-25
I'm an absolute noob so I'm a little extra cautious,,, still I dont like to see my resources at 3/4 full with updates daily

---

### Post by Psumi on 2010-03-25
> **captain.ratsie said:**
> I'm an absolute noob so I'm a little extra cautious,,, still I dont like to see my resources at 3/4 full with updates daily

In terminal, if you want to find out what a package is:

**apt-cache show <package_name>**

Also search synaptic if you want a GUI alternative.

---

### Post by captain.ratsie on 2010-03-25
the problem here is even if it tells me what it is will I know if I need it there ,,,synaptic was where I was when I had to step away ,computer janitor is'nt agressive enough,but I'm too new to know where to cut, ,,I just set up 9,10 on a eee 701 4g but I dont understand shell at all. so I'm stuck in gui-vill for a bit,,, just d/l the beginers guide and its very good ,but small ,I tried the idiots guide to linux but it made a bunch of jumps I couldn't follow ,,, still learnin,,, meanwhile update manager is yellin at me to update cups and I dont even have a printer...and like I said my resources ae 3/4 full with just the os ,,,gona get nbr as soon as it comes out of beta..arrrrg

---

### Post by captain.ratsie on 2010-03-25
sorry for snivelin ,, the cuve is still pretty steep ,,, thank you for your reply

---

