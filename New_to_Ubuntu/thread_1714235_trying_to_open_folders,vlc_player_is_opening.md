---
title: "trying to open folders,vlc player is opening?"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by lalitha niharika on 2011-03-25
i am trying to open home folder or other folders from places,immediately vlc player is opening, for some folders after clicking vlc is playing some song,for other folders there is a vlc msg,"could not find suitable plugin".if i go to computer,from there i am able to open home, other folders.i was able to open all folders after uninistalling vlc player.then again i installed vlc,same problem occured again.i need vlc.what would be the reason for this,how can i correct this?thanks in advance

---

### Post by ~Plue on 2011-03-25
right click a folder on the desktop >> open with other application >> choose 'file browser' and check 'remember this application for folder files'

or press alt+F2 and enter 
```

gedit .local/share/applications/mimeapps.list

```

then delete the line *'inode/directory=.....' *and save the file

---

### Post by lalitha niharika on 2011-03-25
thanks,prob solved:D

---

