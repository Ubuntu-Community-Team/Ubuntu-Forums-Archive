---
title: "How i save my data!?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by mountdiat on 2010-09-24
first ...i formate my hard disc ....ok
then when I install ubntu hi do this 
---make partition 50g for root 
---another partition /home 
---last for swap area ....ok
the question.....if i install ubuntu again in the first partition and select not formate....are all my data saved at the second partition will removed....as home is apart of root ???????????
---if yes.. how can i save my data although all selections at formate screen are apart of root:confused:

---

### Post by mountdiat on 2010-09-24
How pleas?

---

### Post by TCHebb on 2010-09-24
When you format, it does not matter where your partitions are set to mount. All other partitions will be kept intact if you format the first one. After formatting, just set the second one to mount as /home again and your data will be there.

---

### Post by HermanAB on 2010-09-24
If you ensure that all your data is in /home, then you can re-install without formatting /home and everything will be retained.  However, watch out for database programs like MySQL or Apache web server, that save their data in /var.

---

