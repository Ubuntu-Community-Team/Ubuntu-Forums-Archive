---
title: "Home folder mistaken for desktop folder"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by The_Proffessor on 2009-11-11
Ok, so I'm running 8.09 and my desktop folder seems to have run off somewhere and the files on the desktop are in the home folder. I'm sure this is so painfully simple to fix but I can't figure it out. 

I figure I create a desktop directory and somehow either enter a terminal command or change some manner of setting to make it my default folder. 

It's not really a practical problem so much as it is an aesthetic one. I like having a clean, icon free desktop. And if I were to delete these icons I'd loose my documents, pictures, etc.

---

### Post by kelvin.illa on 2009-11-11
The files on your desktop are missing but the same files on your desktop folder in nautilus are there; am I getting it?

---

### Post by The_Proffessor on 2009-11-11
no, my desktop folder is missing and the contents of my home folder are on my desktop.

---

### Post by lisati on 2009-11-11
Which distro are you using? AFAIK Ubuntu didn't come out in an 8.09 version.

---

### Post by The_Proffessor on 2009-11-11
8.10, sorry. got em mixed up.

---

### Post by darthmob on 2009-11-11
Have a look at this post: [http://ubuntuforums.org/showpost.php?p=2228967&postcount=2](http://ubuntuforums.org/showpost.php?p=2228967&postcount=2)
Instead of ticking it you most likely have to untick it. 

quoted from the description:
> If set to true, then Nautilus will use the user's home folder as the desktop. If it is false, then it will use ~/Desktop as the desktop.

// EDIT:
Having a clean desktop is actually quite simple to achieve. In the same directory as the option mentioned above is the setting show_desktop. Untick it and it won't show any icons on your desktop anymore but you can still save files in ~/Desktop.

---

### Post by The_Proffessor on 2009-11-11
ok...at the risk of sounding like a complete noob, I have no idea what the gconf editor is or how to open it.

---

### Post by Terry of Astoria on 2009-11-11
Just type gconf-editor at the terminal, and hit enter to start the gconf-editor.

---

### Post by The_Proffessor on 2009-11-11
woo! it is done! Thanks to all for your fast help.

---

