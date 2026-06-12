---
title: "wakeonlan without having to type the MAC address?"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by jeeves on 2008-02-02
I was wondering if there was a way I can wake computers  on my network without having to type the MAC address. It's a bit tedious having to open up a text file where I keep the MAC addresses and copy the desired address into a terminal.

I tried making a hidden text file in my home directory with a single MAC address inside,  and then running the command:

```
wakeonlan | cat .hiddentextfile
```
*But that did not work*

**Any other ideas?**

---

### Post by jeeves on 2008-02-02
Funny how the process of formulating a question helps one answer it. Shortly after posting the question I  thought up something that works:

make a textfile with this as it's contents:
```

wakeonlan XX.XX.XX.XX
```
***Note - replace "XX.XX.XX.XX" with the actual MAC address of the computer you want to wake***

Save the text file as something like "**wakecomputerA**" and make it executable by running "**chmod u+x wakecomputerA**"

Now *computer A *can be started  by executing the text file as script:
```

./wakecomputerA
```

**If you have a better method, I would still like to hear it.**

---

