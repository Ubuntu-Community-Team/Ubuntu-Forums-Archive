---
title: "black screen after  booting, resume image normal boot - tty1"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Liverhead on 2009-11-10
Hello, I am really stuck, all of a sudden ubuntu wont boot up to the desktop as the Ubuntu images comes up and bar goes accross the full distance then the screen goes black. Also screen seems to be bigger than my monitor as i cant read the caracters to the far left all i can see below by the way Drahcir is my username 
 
out after 60 seconds.
Drahcir tty1
n:

I cant work out what i need to do, i have tried my username my password every thing i think of.
 
i would happily reformat the bugger but i cant even work out how to do that!!! any help would be greatlyappreciated.
 
Rich

---

### Post by saphil on 2009-11-28
I had something similar happen on one of my boxes.  
For some reason the GUI was loading before the Hardware Abstraction Layer
I wrote it up here [http://wolfhalton.info/2009/02/23/mysterious-ubuntu-810-log-in-problem-solved/](http://wolfhalton.info/2009/02/23/mysterious-ubuntu-810-log-in-problem-solved/)
Yours may be similar.  The issue was the links in /etc/rc2.d 
You can look at these in tty1.  If you could print the content of that folder to a file and upload it here, it would be easier to see if the problem was there (presuming you didn't just reformat and try again).  
```
ls /etc/rc2.d > $HOME/links.txt 
```

---

