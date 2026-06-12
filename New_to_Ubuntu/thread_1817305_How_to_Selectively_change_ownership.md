---
title: "How to Selectively change ownership?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-08-03
I have a folder with thousands of files. Some files are owned by User1, some by User2 and some by root. I would like to change ownership of only User1 files to User3. Can it be done?

---

### Post by Wim Sturkenboom on 2011-08-03
read *man chown*

```

wim@desktop-01:/home/fortyfourgalena/testje$ ls -l
total 0
-rw-r--r-- 1 wim             fortyfourgalena 0 2011-08-03 13:26 abc
-rw-r--r-- 1 fortyfourgalena fortyfourgalena 0 2011-08-03 13:26 def
-rw-r--r-- 1 fortyfourgalena fortyfourgalena 0 2011-08-03 13:26 xyz
wim@desktop-01:/home/fortyfourgalena/testje$ **sudo chown --from=fortyfourgalena liza ***
wim@desktop-01:/home/fortyfourgalena/testje$ ls -l
total 0
-rw-r--r-- 1 wim  fortyfourgalena 0 2011-08-03 13:26 abc
-rw-r--r-- 1 liza fortyfourgalena 0 2011-08-03 13:26 def
-rw-r--r-- 1 liza fortyfourgalena 0 2011-08-03 13:26 xyz
wim@desktop-01:/home/fortyfourgalena/testje$ 

```

---

### Post by Guruprasad on 2011-08-03
Perfect....
Thank you very much....

---

