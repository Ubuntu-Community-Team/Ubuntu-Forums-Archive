---
title: "I've searched on the forums, still need help w/printer"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by herbertg on 2009-04-18
I'm trying to get my brother MFC240c to work but I'm having issues trying to force my  
sudo dpkg -i --force-all mfc240clpr-1.0.1-1.i386.deb

error processing mfc240clpr-1.0.1-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc240clpr-1.0.1-1.i386.deb

This file is sitting right on my desktop. I know I'm not typing it wrong.

---

### Post by mikewhatever on 2009-04-18
You have to move to the Desktop first with **cd Desktop** command. Note the capital D there.

---

### Post by jbrown96 on 2009-04-18
Mikewhatever is right. You should also try to just install it normally first; only force it if it won't play nice.

---

### Post by cariboo on 2009-04-18
Why not double click the file and let gdebi handle the installation, it will also install any dependencies if needed.

Jim

---

