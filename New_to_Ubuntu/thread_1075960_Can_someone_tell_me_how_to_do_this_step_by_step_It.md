---
title: "Can someone tell me how to do this step by step? It seems easy, but I'm new :/"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by gymophett on 2009-02-20
Emerald crashes a lot on mine. And this can fix that, but I'm not so sure of how to do it.

[http://ubuntuforums.org/showthread.php?t=599539](http://ubuntuforums.org/showthread.php?t=599539)

Thanks for you guys help :]

---

### Post by taurus on 2009-02-20
Create ~/bin directory to store that file.

Applications -> Accessories -> Terminal
```
mkdir ~/bin
```
Now, change to that new directory

```
cd bin
```
and create a file called _emerald.sh_ with a text editor.
```
gedit emerald.sh
```
Add these lines to that gedit editing window.

```

#!/bin/bash

while true; do emerald --replace; sleep 1; done &

```
Save it and close down gedit window.  Now, you need to change the permissions on that file so you can execute it.

```
chmod 755 emerald.sh
```
Next, you need to add ~/bin to your path in ~/.bashrc so you can run emerald.sh anywhere you want without using the full path.

```
gedit ~/.bashrc
```
And add these two lines to the end of it.

```
PATH=$PATH:~/bin
export PATH
```
Save it and source your ~/.bashrc.

```
source ~/.bashrc
```
That's it.

---

### Post by gymophett on 2009-02-20
> **taurus said:**
> Create ~/bin directory to store that file.

Applications -> Accessories -> Terminal
```
mkdir ~/bin
```
Now, change to that new directory

```
cd bin
```
and create a file called _emerald.sh_ with a text editor.
```
gedit emerald.sh
```
Add these lines to that gedit editing window.

```

#!/bin/bash

while true; do emerald --replace; sleep 1; done &

```
Save it and close down gedit window.  Now, you need to change the permissions on that file so you can execute it.

```
chmod 755 emerald.sh
```
Next, you need to add ~/bin to your path in ~/.bashrc so you can run emerald.sh anywhere you want without using the full path.

```
gedit ~/.bashrc
```
And add these two lines to the end of it.

```
PATH=$PATH:~/bin
export PATH
```
Save it and source your ~/.bashrc.

```
source ~/.bashrc
```
That's it.

Thanks! Great step by step!

---

