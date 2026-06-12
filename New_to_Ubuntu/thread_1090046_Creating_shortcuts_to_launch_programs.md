---
title: "Creating shortcuts to launch programs"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-07
Hi,

Here's a tricky one for you......

Creating a shortcut to launch a program is USUALLY a fairly easy, straightforward task.......


BUT (and it's a very big but)...........

What do you do when the target file that  is in a folder location such as this?

(The bold type is the command entered)
(The [COLOR="Red"]red[/COLOR] is the complete folder that the target file is contained in)
So the file is actually in "SQuirrel SQL Client"....WITH SPACES BETWEEN THE WORDS.

**cd usr**
/usr$ **cd local**
/usr/local$ **dir**
bin  etc  games  include  lib  man  sbin  share  **[COLOR="Red"]SQuirreL\ SQL\ Client[/COLOR]**	src
:/usr/local$ 

:popcorn:

---

### Post by Toxicity999 on 2009-03-07
Quotes around the path. As in:
cd "/usr/local/path with spaces in it/"

---

### Post by laidback on 2009-03-07
Try putting the file name between quotes, i.e. 'filename'

---

### Post by ekaqu on 2009-03-07
> **mistypotato said:**
> "SQuirrel SQL Client"....WITH SPACES BETWEEN THE WORDS.

...
**[COLOR="Red"]SQuirreL\ SQL\ Client[/COLOR]**

To use a file or dir that has spaces, just use a \ right before the white space.

an example from my own computer:
```

cd /media/FreeAgent\ Drive/Random/Random\ Awesome\ Vids/

```

This takes me to the location "/media/FreeAgent Drive/Random/Random Awesome Vids/"

or use ""s around the whole thing

---

