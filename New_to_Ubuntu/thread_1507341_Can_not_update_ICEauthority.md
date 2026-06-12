---
title: "Can not update ICEauthority"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by paul88 on 2010-06-11
When I log in I get the message can not update .ICEauthority . What is this? is it something to be concerned about?

Thanks

---

### Post by Gone fishing on 2010-06-11
This is usually an permissions ownership problem and can probably be fixed with:

sudo chown -R yourusername /home/yourusername

have a look at

[http://ubuntuforums.org/showthread.php?t=1447544&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1447544&highlight=ICEauthority)

---

