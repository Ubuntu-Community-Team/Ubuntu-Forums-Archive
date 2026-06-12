---
title: "Real noob question"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Old-un on 2011-04-19
I am using XChat and i would like to change the background theme but i can't find the XChat folder? Could someone tell me the path to this folder please.

---

### Post by philipballew on 2011-04-19
To search for a file you'll go to places, and then search for files. it could be that its a hidden folder in your home directory. you would click Places > home folder then when that open pressing ctrl+h shows hidden folders. Did you find a website that told you to do it? If so, send me the link and i will walk you through it.

---

### Post by Old-un on 2011-04-19
Ok! I want to change the background theme in Xchat and in order to do so i have got to move two files 'colors.conf' and 'pevents.conf' to a temporary directory. Trouble is i can't find where they are? I have gone to Applications => Accessories => Search For Files and typed in xchat but i still cannot find them?

---

### Post by Anuovis on 2011-04-19
They are likely to be hidden so you need to enable your search to look for hidden files if there is such an option.

In this particular case, you need to go to your Home folder (named after your login name), then press ctrl+h to show hidden files, find a folder named *.xhcat2* or similar to that and peek inside. Should be there.

---

### Post by josephmills on 2011-04-19
I don't have your answer but they might   freenode #xchat   and freenode #freenode

---

### Post by nitstorm on 2011-04-19
Try this:
To look for the colors.conf file, that should display the file path
```
locate colors.conf
``` 

To look for the pevents.conf file:
```
locate pevents.conf
```

---

### Post by Old-un on 2011-04-19
Did as nitstorm suggested and opened a terminal and typed: locate colors.conf and then i used cd ~/.xchat2 and that was it! Thanks for all the help folks it really was appreciated.

---

### Post by philipballew on 2011-04-19
if this is solved can you mark it as solved.

---

### Post by nitstorm on 2011-04-20
> **Old-un said:**
> Did as nitstorm suggested and opened a terminal and typed: locate colors.conf and then i used cd ~/.xchat2 and that was it! Thanks for all the help folks it really was appreciated.

Awesome!

---

