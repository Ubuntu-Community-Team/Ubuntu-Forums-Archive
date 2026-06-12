---
title: "install Zencart on LAMP"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by flameash on 2010-12-02
hello everyone.

newbie here. pre-thx to everyone on the forum; coz i got my LAMP work now by following threads.

ok. so im trying to set up zen cart on my test lamp server before uploading to the actual webserver. and now im stuck at the progress of installing zen.

apache2 installed
mysql installed
php5 installed
phpmyadmin installed

and i can access phpmyadmin page fine

i'v been trying to install zen by the following command:
sudo wget  "http://sourceforge.net/project/zencart/CURRENT_ Zen Cart  1.3.x Series/Zen Cart v1.3.9 - Full  Release/zen-cart-v1.3.9h-full-fileset-11026010.zip/download"

the url inside "" is the url i got from zen download page.

but couldnt get it to work.

am i doing something wrong?

---

### Post by zcwilt on 2010-12-08
Hi

try this link 


```

sudo wget --output-document=zen-cart-139h.zip  "http://downloads.sourceforge.net/project/zencart/CURRENT_%20Zen%20Cart%201.3.x%20Series/Zen%20Cart%20v1.3.9%20-%20Full%20Release/zen-cart-v1.3.9h-full-fileset-10262010.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fzencart%2Ffiles%2FCURRENT_%2520Zen%2520Cart%25201.3.x%2520Series%2FZen%2520Cart%2520v1.3.9%2520-%2520Full%2520Release%2F&ts=1291803328&use_mirror=garr"

```

---

### Post by flameash on 2010-12-09
Thank you very much for responding. (Especially posting that long code)

I downloaded zen successfully by following your code :)

Could you explain that how did you get the "http://downloads........." long link from?
Really appreciated.

---

