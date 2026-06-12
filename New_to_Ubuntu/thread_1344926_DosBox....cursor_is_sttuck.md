---
title: "DosBox....cursor is sttuck"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by viiip on 2009-12-03
Hii !!  Am using DosBox to run Turbo c++,But the cursor could not be moved using arrow keys.I have to use mouse to take it to required position.Though TAB and ENTER are working fine.How can i solve this?I searched other forms and found about ctrl+f10 which is used to free stuck mouse pointer but i could not find any key combinations to take out the stuck cursor.

---

### Post by rCXer on 2009-12-03
See [this thread](http://ubuntuforums.org/showthread.php?t=1248716).

---

### Post by viiip on 2009-12-04
hii..thanks for the link.But when i tried to install dosbox -.73 i got this error - "Dependency is not satisfiable: libstdc++6(>=4.4.0)".I have no idea what this means and how to solve this error.I tried to download it again but still the same error is coming.Am using jaunty,could it be the problem??and ya i have removed dosbox.72.

---

### Post by rCXer on 2009-12-04
Try installing it from [playdeb](http://www.playdeb.net/updates/?q=dosbox). 
 
If that doesn't work, you could just stick with dosbox 0.72 and use this workaround:
* In the terminal reinstall dosbox 0.72 and run it using...
```

sudo apt-get install dosbox
dosbox

```
* In the dosbox prompt, type... 
```

config -writeconf dosbox.conf

```
... This should create a "/home/Yourame/dosbox.conf" file
* Open dosbox.conf and scroll down to the line that says...
```

usescancodes=true

```
...and change it to...
```

usescancodes=false

```
* Restart dosbox

---

### Post by viiip on 2009-12-05
It worked [:)]!!!Re installation gave the same problem but by changing the value "usescancodes=false",it started working fine...but it is quite slow...may be it misses the original DOS...
Thanks again..

---

