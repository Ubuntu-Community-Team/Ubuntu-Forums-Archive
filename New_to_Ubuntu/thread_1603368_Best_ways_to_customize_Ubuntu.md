---
title: "Best ways to customize Ubuntu"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by ironic.demise on 2010-10-22
On my 10.04 install I had a mouse and window borders working.
I would like to know how to install metacity themes and splash screens?
At gnome-look:
[http://gnome-look.org/content/show.php/Function+%26+Lambda?content=133074](http://gnome-look.org/content/show.php/Function+%26+Lambda?content=133074)

This tells you to untar the files to .themes
```
To install (replace tar file with appropriate file):
    
    # install locally 
    tar xfz Lambda-{{version}}.tar.gz -C ~/.themes
```
My files is a .tar.bz2, I tried the same command with that file and it failed. I manually removed the files from the .tar.bz2 and they are all also .tar.bz2; Inside each .tar.bz2 there will be a readme, generic .png files and sometimes a .theme file.

I can't find any documentation on gnome-look, could somebody point me in the right direction or send me somewhere with some information on ubuntu gui customization?

Just want to get some individual and nice aesthetics working.

---

### Post by GabrielYYZ on 2010-10-22
you could use archive manager and extract the contents to /.themes, as it says here: [https://help.ubuntu.com/community/FileCompression#GNU%20Tar%20bzip2%20%28.tar.bz2%29](https://help.ubuntu.com/community/FileCompression#GNU%20Tar%20bzip2%20%28.tar.bz2%29)

also, Chief Bandits are awesome. :guitar:

edit: oh and a if you go down a bit in that same page it says "extracting a tar.bz2 file" and says how to do it in terminal. i missed it the first time i checked, thought i should give a heads up.

---

### Post by ironic.demise on 2010-10-22
> **GabrielYYZ said:**
> you could use archive manager and extract the contents to /.themes, as it says here: [https://help.ubuntu.com/community/FileCompression#GNU%20Tar%20bzip2%20%28.tar.bz2%29](https://help.ubuntu.com/community/FileCompression#GNU%20Tar%20bzip2%20%28.tar.bz2%29)

also, Chief Bandits are awesome. :guitar:

edit: oh and a if you go down a bit in that same page it says "extracting a tar.bz2 file" and says how to do it in terminal. i missed it the first time i checked, thought i should give a heads up.

We have another MSer ;)
Glad to see a fellow CB around, though I've not played in a little while.
I'll take a look, thanks for the heads up... They should just appear in my available themes after that, no?

---

### Post by GabrielYYZ on 2010-10-22
judging by what's on my computer, i'd say the theme file should go in /usr/share/themes/*name of theme* and the png files should go in /usr/share/themes/*name of theme*/bitmaps. a better idea is unpacking the archive and reading the readme, if it's still confusing, post again and we'll go from there. 

i haven't used gnome-look themes, so i'm really not an authority... however, i can vouch for ubuntu tweak: [http://www.ubuntugeek.com/ubuntu-tweak-0-5-7-released-with-ubuntu-10-10-maverick-ppa-updates.html](http://www.ubuntugeek.com/ubuntu-tweak-0-5-7-released-with-ubuntu-10-10-maverick-ppa-updates.html) << that's a guide to installing it, in the application center there are various theme packs which are considerably easier to install (you just select them, apply them and use them) 

hope this helps.

---

### Post by ivarn on 2010-10-22
to install metacity themes, drag and drop the gz archive to Theme (right click > change the background > theme). you can also click the install button and browse for the file.

---

### Post by ironic.demise on 2010-10-22
I read the readme,  no dice...
I'll try gnome tweak instead.
I also tried placing the downloaded the .tar, the contents of .tar (more tars) and the theme folder, also no dice.


++1 to Tweak, thankyou all.

---

### Post by frt975 on 2010-10-22
Ignore the command line directions. Just go to System -> Preferences -> Appearance and there should be a button in the bottom right that says install. Click on it and find your tar.bz2 file.

---

