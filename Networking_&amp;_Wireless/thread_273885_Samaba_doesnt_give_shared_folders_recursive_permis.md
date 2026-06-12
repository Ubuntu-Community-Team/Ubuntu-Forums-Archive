---
title: "Samaba doesnt give shared folders recursive permissions?"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by NoTiG on 2006-10-08
not sure if this is a bug.. but when i share a folder, i want to share its contents and subfolders as well. however when i share a folder with samba, only the folder and none of the subfolders get permitted. that seems wrong to me... is that a bug or a usability "feature"

---

### Post by wieman01 on 2006-10-09
No, this has to do with folder permissions & ownership. You have add the corresponding permissions by using "chown", "chgrp", and "chmod", thus changing the read/write permissions & ownerhip of your files & folders. 

Samba is just as powerful as your Linux system let's it to be if you know what I mean.

---

