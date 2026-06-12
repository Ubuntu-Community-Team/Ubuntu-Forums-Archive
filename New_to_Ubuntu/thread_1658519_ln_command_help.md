---
title: "ln command help"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2011-01-02
Seems I fail at making them
i am trying to make a link named www in /var that points to /home/$USER/public_html
these are folders BTW

---

### Post by AlphaLexman on 2011-01-02
Is your /home/$USER on a separate partition or filesytem from /var?

---

### Post by pqwoerituytrueiwoq on 2011-01-02
same partition

---

### Post by AlphaLexman on 2011-01-02
Then this should work:
```
sudo ln -s /home/$USER/public_html/ /var/www/
```

---

### Post by pqwoerituytrueiwoq on 2011-01-02
thanks 
seems no slash goes after www

---

