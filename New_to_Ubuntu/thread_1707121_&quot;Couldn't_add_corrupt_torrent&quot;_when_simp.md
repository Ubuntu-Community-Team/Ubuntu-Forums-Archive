---
title: "&quot;Couldn't add corrupt torrent&quot; when simply trying to browse folders"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by pr1972 on 2011-03-14
Every time I try to browse a document folder - downloads, home, desktop, music, etc. - I get a message that says "Couldn't add corrupt torrent."  All I want to do is find my files! In the "preferences" section, the "automatically add torrents from" box is UNchecked.

---

### Post by ~Plue on 2011-03-14
that could be a problem with file associations,
*press alt+F2 and run[FONT=monospace]
[/FONT]```
gedit .local/share/applications/mimeapps.list
```and delete the line saying 
```
inode/directory=.....
```

*OR right click a folder on your desktop (create one if you dont have) >> open with other application >> file browser >> check 'remember this application for.......'

---

### Post by pr1972 on 2011-03-15
Thanks, ~Plue!  Worked perfectly!

---

