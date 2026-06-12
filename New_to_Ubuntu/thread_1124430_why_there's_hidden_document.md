---
title: "why there's hidden document"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by mymaydayya on 2009-04-13
I found every time after I save a document, for example "ubuntu.awk", and there will be a hidden document called "ubuntu.awk~"

How to fix it, or there's no problem about this?

Thanks everyone I love ubuntu.

---

### Post by Hospadar on 2009-04-13
It's not a problem,
many editors save these backup copies periodically in case your machine looses power or the program crashes, so that you can recover your work.  Depending on the editor, you may or may not be able to disable this behavior.

If you want to remove all such files from a folder, 
rm *~
(which will remove all files ending in ~)

---

### Post by Kosimo on 2009-04-13
That happens to me as well some times and I'm also curios to know what is it.

---

### Post by Kosimo on 2009-04-13
> **Hospadar said:**
> It's not a problem,
many editors save these backup copies periodically in case your machine looses power or the program crashes, so that you can recover your work.  Depending on the editor, you may or may not be able to disable this behavior.

If you want to remove all such files from a folder, 
rm *~
(which will remove all files ending in ~)

Done ;)

Thank you!

---

