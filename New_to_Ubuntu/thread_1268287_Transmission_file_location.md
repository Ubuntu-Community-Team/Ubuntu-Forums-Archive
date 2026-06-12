---
title: "Transmission file location"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Muscovy on 2009-09-16
I've always been really annoyed by torrents going into really unappealingly named folders. Yesterday I found a way to make it put the file just plain old in the location you selected. For example, the Ubuntu iso is just in ~/Installers/Ubuntu, instead of ~/Installers/Ubuntu/HugeString. How do I make it do that? :confused:

---

### Post by Bölvaður on 2009-09-16
open Transmission

Edit &#8594; Preferences
Destination folder : browse to your preferred location

---

### Post by Muscovy on 2009-09-16
'fraid that doesn't work. I still have a folder like "Fedora-11-x86_64-Live-KDE" in the location I wanted to drop the iso.

---

### Post by wojox on 2009-09-16
It's going to create a folder when you download it.

---

### Post by lovinglinux on 2009-09-16
> **Muscovy said:**
> 'fraid that doesn't work. I still have a folder like "Fedora-11-x86_64-Live-KDE" in the location I wanted to drop the iso.

I'm not sure about Transmission, but as far as I remember, it doesn't create folders if the torrent content does not have multiple files inside folders. Have you checked if the torrent file you are downloading does not have multiple files?

---

### Post by Muscovy on 2009-09-16
Oh! That's why it went funny when I tried it today!

Unfortunately, removing reduntant files like readme, leaving only the iso still gives me the folder.

---

### Post by lovinglinux on 2009-09-16
> **Muscovy said:**
> Oh! That's why it went funny when I tried it today!

Unfortunately, removing reduntant files like readme, leaving only the iso still gives me the folder.

Yes, it is how it works. Even if you do not download all files, it will create the folders specified by the torrent metadata.

---

