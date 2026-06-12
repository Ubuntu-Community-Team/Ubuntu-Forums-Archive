---
title: "Creating Right-click scripts!"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-06-23
How to create a script that contains something like send to or convert to etc,
any guide or help for that ?

---

### Post by sisco311 on 2010-06-23
Are you talking about nautilus scripts?

[uhelp]community/NautilusScriptsHowto[/uhelp]

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by MBG1987 on 2010-06-23
thanks
what i need to do is to convert a set of .png image to .gif using right-click script in nautlis, the normal way to do so is to cd to the directory and type:

```
convert -delay 200 -loop 0 *.png timevault.gif
```
So who to accomplish this task using the prior way

regards

---

### Post by kaibob on 2010-06-23
Place the following in a text editor, save it with a script name of your choice, and make the file executable. 

```
#!/bin/bash

convert "$@" -delay 200 -loop 0 output.gif
```

Then, move the script to the following directory:

/home/username/.gnome2/nautilus-scripts

To use this script, open nautilus, select and right-click on the PNG files that will be included in the GIF, and select the script name after "Script" in the right-click menu. It will create output.gif in the same directory. I tried this and it worked fine.

---

### Post by MBG1987 on 2010-06-23
Oh thank you, it works fine

---

