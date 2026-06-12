---
title: "Open with list"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-23
How do I edit the open with list in UBU 9.10. THX.:confused:

---

### Post by Morbius1 on 2009-12-23
I've read your post multiple times and I'm sorry but I have no idea what you're talking about. Could you be more specific?

You're trying to edit "the open" - what is "the open"?

---

### Post by audiomick on 2009-12-23
I would read it like this:

How do I edit the "open with" list

but I could be wrong.

A little bit of punctuation goes a long way, eh... ;)

---

### Post by jnmjr on 2009-12-23
Sorry about my punctuation, it should read "open with" list, as when you right click on a file there's a list of apps. you can choose to open. I would like to edit this list but do not know how or what the file name is that contains this list. THX.

---

### Post by Morbius1 on 2009-12-23
Ah, this is a rather unintuitive process.

Open Nautilus and go to the file you want the "open with" options modified. Right click and choose "Properties" > "Open With"

There you can add, delete, and reset.

Sorry for the confusion - not having a good day here. :redface:

---

### Post by jnmjr on 2009-12-23
Not exactly what I want to do, what I want is to edit  the list itself, for some reason many of the apps. are listed twice and many I will never use, there must be a file name for this list but I don't know where it is or how to find it. THX.

---

### Post by Morbius1 on 2009-12-24
You could play around with : /home/user_name/.local/share/applications


If I remember correctly you'll need to reboot or restart x for the changes to take.

---

### Post by jnmjr on 2009-12-24
Thanks for the info , this led me to "usr/share/applications", that's where all the exe files are located, I just deleted the ones that where doubled and problem solved. THX again:P

---

### Post by freacert on 2010-12-26
I figured out it are both locations to be edited.

as sudo nautilus go to /usr/share/applications
and in your home folder, go to share/applications and this way the "open with" list can be cleared of all the unnecessary apps.

---

