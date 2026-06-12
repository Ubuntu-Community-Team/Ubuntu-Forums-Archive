---
title: "Python"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-04
Hi
 Is Python already installed in Ubuntu 9.04 and if so what version is it?
I want to rlook at a game and it says I need to click on file ardentryst.py
but nothing happens when I do.

Thanks

---

### Post by _Purple_ on 2009-06-04
Run this in terminal to find which version of python you have 
```
python -V
```

The file you are trying to run, is it executable? Go to the directory which contains the file and run 
```
chmod a+x ardentryst.py 
```
Then double click.

---

### Post by Anybloodyid on 2009-06-04
OK it's Python 2.6 so how do I get the game to run?
Here's the instructions from the site
 There will be a folder called 'Ardentryst'. Inside this directory, execute ardentryst.py with Python.

---

### Post by amingv on 2009-06-04
Also you may want to check if the file is marked as executable. You can make it executable with:

```
chmod a+x ardentryst.py
```

Is this a console game? if it is, then try running it from the console.

If it's not a console game, it may need pygame or another module/dependency. You'd need to install that manually.

If you give me a link to the game I'll check it out for you.

> **Anybloodyid said:**
> execute ardentryst.py with Python.

To do that last bit, try

```
python ardentryst.py
```

---

### Post by Anybloodyid on 2009-06-04
Thanks Amingv just been back to the site and I do need to get Pygame first.

Here's a link if you want to look anyway
 [http://jordan.trudgett.com/](http://jordan.trudgett.com/)

---

