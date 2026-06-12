---
title: "Where is my Recycle bin"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by yaacovk on 2009-11-14
Hello/
My system is 9.10
My Recycle bin was disappear from my desktop.
what should i do.

Thanks.
Yaacov.

---

### Post by Paqman on 2009-11-14
Right click on any panel > add to panel > I think it's called "trash applet".

---

### Post by J-Buntu on 2009-11-14
If desktop: open a terminal or press alt-F2 and type 'gconf-editor' (no quotes) and press return. In the Configuration Editor window, navigate to apps > nautilus > desktop and tick trash_icon_visible.

If panel: right-click on panel, select 'Add to Panel' and choose 'Deleted Items'

---

### Post by kwacka on 2009-11-14
deleted

---

### Post by dckirba on 2009-11-14
You can also find the files in your trash by
[LIST]
[*]Opening the file manager (click on home or documents and it will open)
[*]Go to your home folder
[*]Press ctrl-h to show hidden files and folders
[*]The folder .trash is your trash folder
[/LIST]
I know this isn't exactly a reply to your question (which was already answered above), but I thought it would be a useful thing to know.

Cheers,
David

---

### Post by dzon65 on 2009-11-14
In 9.10 there is no .trash folder by default.

---

### Post by ajgreeny on 2009-11-14
No, it's now in ~/.local/share/trash/files and has been for the last couple of ubuntu versions, if I remember correctly.

---

### Post by dckirba on 2009-11-15
Thanks guys, I wasn't aware of that. Guess it's time for an update hey :)

Cheers,
David K

---

