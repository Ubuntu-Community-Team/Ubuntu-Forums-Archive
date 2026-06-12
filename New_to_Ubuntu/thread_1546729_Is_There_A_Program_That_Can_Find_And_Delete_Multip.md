---
title: "Is There A Program That Can Find And Delete Multiple Files?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-08-05
I used Catfish to look for files in a folder.  I found about 700 files I want deleted.  Well just ctrl + a then delete right?  Well that won't work, nor would dragging the mouse to highlight them.  Is there another alternative, or do I have to manually delete all of these?

Thanks

---

### Post by Ozymandias_117 on 2010-08-05
You could use ```
find /root/folder/to/start/search -name "*what you want to search for*" -delete
```

Edit: Try it once without -delete before doing it for real to make sure you don't delete something you don't want it to.

---

### Post by bodhi.zazen on 2010-08-05
> **giddyup306 said:**
> I used Catfish to look for files in a folder.  I found about 700 files I want deleted.  Well just ctrl + a then delete right?  Well that won't work, nor would dragging the mouse to highlight them.  Is there another alternative, or do I have to manually delete all of these?

Thanks

With the files selected, Shift + delete

Otherwise, use find as outlined above.

google search how to linux find , there are several tutorials available.

---

### Post by giddyup306 on 2010-08-06
> **bodhi.zazen said:**
> With the files selected, Shift + delete

Otherwise, use find as outlined above.

google search how to linux find , there are several tutorials available.

1) I know how to search with the terminal.  I don't like using it.  2) It won't let me select multiple files in Catfish. 3) For every one question I ask on here, I do at least 10 google searches.  If I wasn't able to find it I ask here.  Telling me to "google search" does no better job than not answering the question at all.  4) I was asking if there was another program available.

---

### Post by HermanAB on 2010-08-06
Find files? Read the man page of the 'find' command.  It will be time well spent.

---

### Post by Zorgoth on 2010-08-06
find is one of the most useful utilities you have.  If you don't like it, learn to :)

---

