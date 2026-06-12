---
title: "Could not initialize the package information? Help"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by freedom? on 2010-05-13
This is what I recently got when I tried to update. Obviously I dont know what to do next, hope someone can help. Hanx!:confused:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'See' is not known on line 2 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by Sealbhach on 2010-05-13
Ok, it refers to Line 2 of your sources.list file. So open up that file and let's see what's in Line 2. You can do that by copying and pasting this command into the terminal:

```
gksudo gedit /etc/apt/sources.list
```

Scroll down to Line 2, and copy and paste whatever it is in your reply.

.

---

### Post by cariboo on 2010-05-13
Could you paste a copy of /etc/apt/sources.list in your next post.

Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

The above command will open the the sources.list in the text editor. Just copy the text and paste it into the post. Using [noparse]```

```[/noparse] tages will make the text a little more readable.

---

### Post by Sealbhach on 2010-05-13
Line 2 in my sources.list is

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
```Make sure you have a "#"  in front of the word "See". I suspect that's what's causing the problem.

.

---

### Post by freedom? on 2010-05-13
Ok there  was no # in front of See. So I'll put one there then re-boot?

---

### Post by freedom? on 2010-05-13
> **freedom? said:**
> Ok there  was no # in front of See. So I'll put one there then re-boot?
Here is line 2 and 3 
#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
newer versions of the distribution.

---

### Post by Sealbhach on 2010-05-14
> **freedom? said:**
> Ok there  was no # in front of See. So I'll put one there then re-boot?

Yeah. There's no need to reboot, just save your change and close the file, then run

```
sudo apt-get update
```

in a terminal then you should be good to go.

.

---

### Post by freedom? on 2010-05-14
> **freedom? said:**
> Here is line 2 and 3 
#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
newer versions of the distribution.
Dont really know what I did, BUT! It updated:P
Thanks for your help all:guitar:\\:D/

---

### Post by freedom? on 2010-05-14
> **Sealbhach said:**
> Yeah. There's no need to reboot, just save your change and close the file, then run

```
sudo apt-get update
```

in a terminal then you should be good to go.

.
Thanks!!!!!!! Much appreciated

---

