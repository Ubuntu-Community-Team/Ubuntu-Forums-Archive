---
title: "Running Two Apps with a Launcher"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by brenan on 2008-12-26
I wanted to make a launcher that ran one of my games and rhythmbox at the same time, but I'm not sure how to do this. I just combined the two commands, but the computer tries to open them in the same terminal, since the first one must close before the other opens. Can I do this?

---

### Post by Dr Small on 2008-12-26
The && command tells the system to run the next command after the previous command has executed with an exit status of 0. Try using **;** between the commands, to run the first one, then the second one.

---

### Post by ercferret18 on 2008-12-26
you could just make two launchers and double click one, then the other...

---

### Post by brenan on 2008-12-26
It did the same thing. I may just make two, but I'd like to do it this way if possible.

---

### Post by Dr Small on 2008-12-26
You can make a script to launch both of them in the background. Here's what I did for a test:

```
#!/bin/bash
#scriptname: script

medit&
gvim&
exit 0
```

Give it executable permissions:
```
chmod +x script
```

And then set your launcher to execute the script.
That should work.

Dr Small

---

