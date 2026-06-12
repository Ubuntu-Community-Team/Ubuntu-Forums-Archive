---
title: "Zenity script"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Dark006 on 2009-03-08
I've got a slight problem with a small script I wrote. What I'm trying to do is have a nautilus script that will save any video saved into memory and using zenity to change the name to what I want. Here is the script thus far
```

#!/bin/bash
name=$(zenity --entry --title="Rename your Video" --text="Please change to desired name ")
cp /tmp/Fla* ~/Desktop/Flash
mv ~/Desktop/Flash ~/Desktop/$name

```

It seems to work fine for one word names of the video(like "dog", "cat", etc..). But if I try to name it anything more than one word it just defaults to name it "Flash".

Does anyone have any ideas on what I could do to fix this?

---

### Post by Jose Catre-Vandis on 2009-03-08
Try using inverted commas for the multiple words? e.g.:

```
mv ~/Desktop/Flash ~/Desktop/"$name"
```

I tested your zenity code line and it does return multiple words, but the mv command probably won't like it

or

Don't type names with spaces, use _ or - between words, might help you later on when you want to do something else.
Takes a while to get into the habit :)

---

### Post by Dark006 on 2009-03-08
Thank you so much Jose Catre-Vandis! The quotes work fine! I don't know why I didn't think of that haha.

---

### Post by Jose Catre-Vandis on 2009-03-08
> **Dark006 said:**
> Thank you so much Jose Catre-Vandis! The quotes work fine! I don't know why I didn't think of that haha.

:)

---

