---
title: "Increasing number of recent documents?"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Gordonbp531 on 2010-12-17
Is there any way of increasing the number of Recent Documents displayed in Places-Recent Documents?

---

### Post by seawolf167 on 2010-12-17
I personally disable my recent documents from displaying anything; I looked around a little and couldn't find any way to increase the number of documents (though someone else may know more)

The .recently-used.xbel simply stores the doc list
There are no entries in gconf-editor (that I could find)
I couldn't find any config files in /etc

This seems to be one of those things that doesn't have a config file of any type to change

---

### Post by hariks0 on 2011-06-26
To set the number of files that appear in Recent Documents, use ```
gedit ~/.gtkrc-2.0
``` and ```
gtk-recent-files-limit=30
``` (replace 30 with the number of files you wish to show).

:guitar:

---

### Post by tc101 on 2012-07-21
I am running 10.04.  Will this work?

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

