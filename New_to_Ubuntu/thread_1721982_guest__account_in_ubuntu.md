---
title: "guest  account in ubuntu ?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-05
i could not figure out how to create an account on my computer which does not has access to my files i-e desktop,documents, music etc.

---

### Post by deathadder on 2011-04-05
> **zaafar said:**
> i could not figure out how to create an account on my computer which does not has access to my files i-e desktop,documents, music etc.
Are all of those files in your home directory? If so you can simply open a file browser can change to /home then right click on your home folder and select "Properties". Then from the Permissions tab change "Folder access:" for others to "None." If the group is anything apart from your username, change "Folder access:" to none aswell. 

Then any other users logged in will not be able to view your files. If your files are split over multiple directories you'll need to go through the same process for each directory.

---

### Post by zaafar on 2011-04-05
worked for me , thanx

---

