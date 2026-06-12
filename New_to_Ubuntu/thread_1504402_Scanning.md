---
title: "Scanning"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by kithey on 2010-06-08
my scanning doesn't work in ubuntu 8.10, once i open the Xsane and click scan it will just exit and nothing will do...what will i do...?Help..

---

### Post by XubuRoxMySox on 2010-06-08
I find [Simple Scan]("http://lifehacker.com/5483366/simple-scan-makes-linux-scanning-beginner+friendly") (available in the Lucid repositories) much easier and nicer. 

It might also be helpful if you post what kind of scanner you have, so that the geekier folks who see this thread will have a little more to go on to help you.

Using *SimpleScan* joyfully,
Robin

---

### Post by kithey on 2010-06-08
my scanner is HP Officejet 6500 all-in-one printer. Before it scan well using xsane, but unfortunately it has been corrupted that is why i reinstall my UBuntu OS. After i installed the Ubuntu 8.10 i tried to scan again using xsane but nothing happens...I didn't install any driver because my computer  automatically detects the printer. I  tried to print and it works...Pls help...

---

### Post by pizza-is-good on 2010-06-08
Look at the [xsane supported devices list]("http://www.sane-project.org/sane-mfgs.html").

if your scanner is there, then it will work, it its not, then it won't. I have an HP scanner that is just not supported. I haven't tried to use it with simple scan.

~pizza

---

### Post by MG Studio on 2010-06-08
MG Studio
'great site here!

---

### Post by Peter09 on 2010-06-09
As a test try opening xsane with sudo, ignore the warnings and see if it works

---

### Post by davidsrsb on 2010-06-09
Why are you trying to use a 2 year old version of Ubuntu?
The 6500 requires hplip and is a bit fussy about library versions

see [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1276078067591+28353475&threadId=1378696](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1276078067591+28353475&threadId=1378696)

---

