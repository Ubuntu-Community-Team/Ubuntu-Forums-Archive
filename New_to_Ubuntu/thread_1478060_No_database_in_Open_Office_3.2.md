---
title: "No database in Open Office 3.2"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by captgadget on 2010-05-09
I did a clean install of Lucid and now I have no Open Office database. Was this eliminated in the new version?

---

### Post by Norm24 on 2010-05-09
No it wasn't eliminated.But I installed 3.2 under Karmic and upgraded to Lucid and I have it.

I used this method to install 3.2:
[http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)

Maybe a fresh install of 3.2 might do the trick?

---

### Post by Sub101 on 2010-05-09
> **captgadget said:**
> I did a clean install of Lucid and now I have no Open Office database. Was this eliminated in the new version?

No, you need to install openoffice database separately, it does not come pre installed.

```
 sudo apt-get install openoffice.org-base

```

---

### Post by Linuxforall on 2010-05-09
Install it from software center, in case you want Sun Java, install that first by enabling lucid partner repository otherwise it will install Open JDK.

---

### Post by Sef on 2010-05-09
> I did a clean  install of Lucid and now I have no Open Office database. Was this  eliminated in the new version?

> No it wasn't eliminated.But I installed 3.2 under Karmic and upgraded to  Lucid and I have it.
No it wasn't eliminated.But I installed 3.2 under Karmic and upgraded to  Lucid and I have it.
 
 I used this method to install 3.2:
 [http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)
 
 Maybe a fresh install of 3.2 might do the trick? 	
I used this method to install 3.2:
[http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)

Maybe a fresh install of 3.2 might do the trick? 	

It just was not installed by default.   The easiest way to install it is this:

Applications > Ubuntu Software Center > Search: type in DATABASE > Top option should be OpenOffice Database > click install

---

