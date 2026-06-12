---
title: "How do I make this file executable..."
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-07
I think I am doing this right. I am starting a new tread because it is a different subject. I would like to make this file executable:

firstprogram.py

It is from the Python Tutorial but I did not see any part on how to make it executable.

---

### Post by bukwirm on 2009-02-07
chmod +x *filename* will make a file executable. Then you can run it by typing ./*filename*

---

### Post by perlluver on 2009-02-07
> **Leo Dragonheart said:**
> I think I am doing this right. I am starting a new tread because it is a different subject. I would like to make this file executable:

firstprogram.py

It is from the Python Tutorial but I did not see any part on how to make it executable.

Simplest way is to right click on it, then go to properties, the permissions tab, and select make executable.

---

### Post by Leo Dragonheart on 2009-02-07
It didn't work. I must be doing something wrong...:(  (I hate the $%^& Terminal right at this moment!!!), but I know I will grow to love it. Thanx for your advise. I did make it executable though by going through the properties like you suggested...

---

### Post by talsemgeest on 2009-02-07
> **Leo Dragonheart said:**
> I think I am doing this right. I am starting a new tread because it is a different subject. I would like to make this file executable:

firstprogram.py

It is from the Python Tutorial but I did not see any part on how to make it executable.
You can make it executable by right-clicking the file, going to the permissions tab and ticking the box "Allow executing file as program." You can also run the program from the terminal without making it executable by typing ```
python firstprogram.py
```

---

