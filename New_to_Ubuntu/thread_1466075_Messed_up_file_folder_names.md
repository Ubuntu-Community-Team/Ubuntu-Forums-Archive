---
title: "Messed up file folder names"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by paker on 2010-04-30
Somehow I have 2 different file folders (DOWNLOADS and DESKTOP) having exactly same content.

One is Places > Home Folder > Downloads.
The other is Places > Desktop (file folder icon, not the shiny desktop icon). 

When I select Places > Desktop, Downloads open. 
Transmission stores everything in Desktop, but actually all go to Downloads.

The way I see, Desktop is a ghost file folder (without content ) that links to Downloads. It exists only in 2 places, 1) Places > Desktop, and 2) Transmission>Edit>Preferences>Save to location>Desktop. 

I also have a separate shiny desktop icon in Places > desktop. This is the real desktop.

I need to either get rid of one or merge the two. Pls help.

---

### Post by RolandFlagg on 2010-04-30
Seems like you have some a soft symbolic link. Do a "ls -ali" in your home Directory and Places, and check for somethign that looks like this: "->" on the last column of Downloads and Desktop. If it's there, then follow these directions, and you should be able to remove the symbolic link.

[http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html](http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html)

---

### Post by paker on 2010-04-30
Both Desktop and Downloads have nothing like "->"

---

### Post by RolandFlagg on 2010-05-01
oh... i'm not sure then, sorry I'm not much of a help :(

---

### Post by paker on 2010-05-02
> **RolandFlagg said:**
> oh... i'm not sure then, sorry I'm not much of a help :(Oh, yes, you helped. You eliminated one of the causes. Thanks.

---

