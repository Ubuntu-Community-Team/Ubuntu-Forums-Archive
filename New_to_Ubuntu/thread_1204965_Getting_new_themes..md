---
title: "Getting new themes."
date: 2009-07-05
forum: New to Ubuntu
---

### Post by PerPPP on 2009-07-05
I know there have already been threads about this but I can't seem to get this to work.  I just got the Ubuntu dekstop edition 9.04 and I am trying to install a new theme.  The specific theme I am looking for is the Mythbuntu theme.  I am pretty sure I downloaded it off of the gnome-look website and I saved the TAR file to my documents folder.  When I try and drag and drop the file to my theme selection screen however, it gives me an error and says its not a valid theme.  What am I doing wrong?  Is there anything I have to install beforehand?  DO I have to extract the downloaded file or something?  Could somebody please help me get the Mythbuntu theme installed on my Ubuntu?  Also I am trying to get a trash shortcut on my desktop and I was wodering if you could help me with that as well.

---

### Post by nothingspecial on 2009-07-05
To get the trash icon on your Desktop hit Alt + F2 and type

```
gconf-editor
```

navigate apps > nautilus > desktop and put a tick in the "trash icon visible" box

As for the theme extract it and see if there is anything in the package that you can install such as another tar.gz folder.

---

### Post by oldos2er on 2009-07-05
Run
```
sudo apt-get update && sudo apt-get install gtk2-engines-mythbuntu
```

---

### Post by PerPPP on 2009-07-05
Thanks for the help guys.  The trash was weird because I had tried this before and it hadn't worked.  It did work this time though so oh well.  As for the theme, I had been extracting the wrong folder into my theme box.  I now have both things working great so thanks for the help you guys!

---

