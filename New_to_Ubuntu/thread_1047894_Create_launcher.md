---
title: "Create launcher"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by inoe on 2009-01-22
cd /home/dhendy/Documents/bainur/TPMI/trunk/ && mongrel_rails start

in terminal it is working , but in the launcher it has following message
[I]
Details: Failed to execute child process 
"cd" (No such file or directory) [/I]

how do i fix this ??? or there's other way to create a launcher??

---

### Post by blueridgedog on 2009-01-22
If you put your commands in a shell script then you can call it with the launcher:

```
#!/bin/bash          
cd /home/dhendy/Documents/bainur/TPMI/trunk/
mongrel_rails start   
```

To make this, 

```
gedit launchrails.sh
```

Then paste in the text above (I am calling it launchrails.sh).

Then in a terminal in the directory in which you placed the file:

```
chmod u+x launchrails.sh
```

Then reference launchrails.sh in the launcher.

---

### Post by inoe on 2009-01-22
thank u , its work now.

---

### Post by blueridgedog on 2009-01-22
> **inoe said:**
> thank u , its work now.

Excellent.  When you want to do more than one thing with a launcher, or an icon for that matter, you can package them in a script...the sky is the limit.

---

