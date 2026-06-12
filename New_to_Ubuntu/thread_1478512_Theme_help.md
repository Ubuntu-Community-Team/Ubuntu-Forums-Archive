---
title: "Theme help"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-05-09
I tried to change my theme preference and clicked on "get more themes on line" in the System>Preferences>Appearance box.

I picked a windows border theme and downloaded it.  I had the option of opening it with the theme installer which I did.  It installed but I didn't know I had to save it and clicked on another theme before saving it.  I tried to install it again the same way and I get an error message

There was an error installing the selected file
"MCity-ClearlooksWithACherryOnTop.tar-9.gz" does not appear to be a valid theme.

I tried saving it, extracting it and installing it with the install button but it doesn't work.  It says it's not a valid theme file.

How can I reinstall this theme?

---

### Post by cubeist on 2010-05-09
it may have been mis-packaged.

two methods
try saving, but don't extract it, then drag the .gz on the theme window (appearances)

or, save it, extract it then manually put the theme contents in your /home/user/.theme folder

---

### Post by ddecator on 2010-05-09
> **dondiego2 said:**
> There was an error installing the selected file
"MCity-ClearlooksWithACherryOnTop.tar-9.gz" does not appear to be a valid theme.


The tar-9 may be throwing it off since it's used to just tar.gz. It might work if you just edit the -9 out of the extension (although I'm not sure if that will break it or not, never seen tar-9 before so I don't know how it's different).

---

### Post by dondiego2 on 2010-05-09
The "-9" part was not in the file that I saved.

I looked in the .theme folder and saw that these files already existed in there.  So I just deleted them and tried installing the tar.gz file again and it worked.  Thank you both for your help!

---

