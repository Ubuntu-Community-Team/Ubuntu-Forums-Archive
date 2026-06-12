---
title: "Something simple."
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Mashai on 2011-07-31
So, you know how in Windows you can create a shortcut, go the the preference tab and change the file path or whatever? The 'start in' box? How do I do that on Ubuntu?

---

### Post by mike555 on 2011-07-31
A launcher (shortcut) on the desktop can be rt. clicked on and show properties ....... a file (image or whatever) can be rt. clicked on and show properties ,like open with etc.
   so I'm not sure what your question is?

if your trying to change what opens a certain file type ,just rt. click on the file and go to properties and set the default opening program.

---

### Post by Mashai on 2011-07-31
Maybe it'll help if I post the instructions I'm trying to follow. Keep in mind that these were written with Windows in mind.
> 
Instructions: 
============================================================================ 
1.) Make sure all the files contained in AMTS.rar are in the same folder, with no other files. 
2.) Create a new shortcut for MUSHClient on your desktop, give it an interesting name. 
[B]3.) Right click on your new shortcut, and click properties. 
4.) In the Start In: box, type in the file path to AMTS 
    i.e.: "C:\Users\David Volin\Documents\Aetolia\AMTS" 
5.) Click ok! 
[/B]6.) Run MUSHClient via your new shortcutNow, I'm running MUSHClient through Wine. Hopefully you see what I'm trying to do here?

...Not knowing the proper terms to even ask questions with makes this much harder than it needs to be, I'm sure -_-'

---

### Post by cybergalvez on 2011-07-31
Since its running in wine the paths would be local windows paths local to that wine instances (~/.wine for the default one. I would write a shell script that changes to the proper directory and then launches your app

---

