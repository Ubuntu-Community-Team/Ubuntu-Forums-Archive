---
title: "Customise Nautilus subfolders columns"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by cacs on 2011-05-25
Hi there.

It is possible apply a customisation to all subfolders (but not to ALL folders)?

I want to customise all music folders but not one by one, is that possible?

Thanx, C.S.

---

### Post by aeiah on 2011-05-25
what do you mean by customise?

---

### Post by Frogs Hair on 2011-05-25
Yes , it is possible to customize folder by right clicking and entering properties . Click on the folder image and then migrate to the custom folders you have downloaded and change the image.

Be aware that if you change icon sets these folders will not change and you will have to do it manually .

---

### Post by cacs on 2011-05-25
> **aeiah said:**
> what do you mean by customise?

Well, by custumise I mean add columns such as bitrate, album, artist etc, but to all "Music" subfolders and not to **all** folders, so i don't want to do it by the "Edit > Preferences" way since i just want to do it to certain folders!

TY, C.S.

---

### Post by AlphaLexman on 2011-05-25
See [this thread]("http://ubuntuforums.org/showthread.php?t=1278985")

---

### Post by cacs on 2011-05-26
Thank you AlphaLexman.
I already have that script.
I'm sorry if I couldn't explain better but what I need is a way to change some folder subfolders without applying it to all system (all folders)!
Is that possible?

TY, C.S.

---

### Post by AlphaLexman on 2011-05-26
> **cacs said:**
> I'm sorry if I couldn't explain better.
Do you mean you want to define all directories in ~/Music/Artist/Album/ to utilize the python script without having to open each directory and manually click each one to activate the python script?

I don't know how to advise that procedure.
 
Nautilus will automatically save the last viewed format for each directory. Apparently you want to preset the directory to invoke the python script.

You may have to write another script to force nautilus to reformat the view for directories below the ~/Music/Artist/Album level.

---

### Post by cacs on 2011-05-27
> **AlphaLexman said:**
> Do you mean you want to define all directories in ~/Music/Artist/Album/ to utilize the python script without having to open each directory and manually click each one to activate the python script?

I don't know how to advise that procedure.
 
Nautilus will automatically save the last viewed format for each directory. Apparently you want to preset the directory to invoke the python script.

You may have to write another script to force nautilus to reformat the view for directories below the ~/Music/Artist/Album level.

Yes that's it! It would be possible by default! I see now it isn't :(
Thank you!

---

