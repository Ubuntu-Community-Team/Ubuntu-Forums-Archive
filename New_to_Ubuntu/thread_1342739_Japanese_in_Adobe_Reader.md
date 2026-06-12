---
title: "Japanese in Adobe Reader"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by cormocodran on 2009-12-01
I needed to open some PDF files with Japanese character in it. I have downloaded the font pack from Adobe's website and tried to follow the steps in [https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto#Acro8.1](https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto#Acro8.1)
However, everytime I entered sudo ./install, it give me
```
 sudo: ./install: command not found
```I'm using Adobe Reader 9, btw.
Any suggestion?

---

### Post by ToshibaLaptoplinux on 2009-12-03
I believe the script name is in capital letters.

INSTALL

---

### Post by cormocodran on 2009-12-08
You were right. It should have been INSTALL. 

Can you help me some more? It seems that I'm stuck in the next step. I'm asked where I installed Adobe Reader, and everytime I entered the right directory, e.g.    /home/cormocodran/Adobe, it keeps on asking where the directory was. I have no idea where I did wrong, I had checked the directory using the step outlined in the help page, i.e. inputting locate /Adobe/Reader9/Resource, and it gives the result of 
```
/home/cormocodran/Adobe/Adobe/Reader9/Resource/Linguistics
```Hence I presume I already entered the right directory.

Thanks.

---

### Post by cormocodran on 2009-12-08
After posting the last reply, it crossed my mind that maybe the problem is because I'm using Reader9. So I googled it, and apparently it aws the issue. My problem was resolved after I downloaded the newer font pack from the following URL. [http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix](http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix)

---

