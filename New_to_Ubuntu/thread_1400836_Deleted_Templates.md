---
title: "Deleted Templates"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by lapor on 2010-02-07
Hello,

I have a bizzare problem. My brother deleted folder Templates. And I have no idea how to create it again. I can create folder and name it "Templates", but it doesn't react like it should. Well, to creat templates.

Could someone tell me how to re-create this folder and to be active.

Thanks!

---

### Post by lapor on 2010-02-08
Anyone?

---

### Post by wojox on 2010-02-08
Edit ~/.config/user-dirs.dirs

and add the Template directory like this:

XDG_TEMPLATES_DIR="$HOME/Templates"

---

### Post by lapor on 2010-02-08
Thank you for your help. I fixed it. It doesn't have the picture on the file, but it works.

Thanks

---

