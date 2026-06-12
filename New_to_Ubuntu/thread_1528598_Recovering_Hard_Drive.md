---
title: "Recovering Hard Drive"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by merico01 on 2010-07-10
I have used Testdisk and photorec to re-build the partition and recover the data. The recovery resulted in about 285 directories full of .txt file and unreadable UTF 16 files. can someone explain to me what happened, and what went wrong?

---

### Post by bodhi.zazen on 2010-07-11
Nothing went "wrong", these tools, testdisk and photorec, are "low level".

They recover the raw data if you will and dump it into generic files. file1.txt , file2.txt , etc.

You then need to examine each file and see if the contents are anything more then jibberish , and if so, what you want to call it and where to save it.

You can use tools such as grep to try to identify key pieces of say text. Image files are more one - by  - one.

---

### Post by mapes12 on 2010-07-11
Try this. Some of it is commercial but I guess it's a question of how important your data is:-

[http://www.runtime.org/](http://www.runtime.org/)

---

### Post by bumanie on 2010-07-11
Near the bottom of [this page]("http://www.linux.com/archive/feed/56588"), there is a section that gives clues on sorting files - it may help a little - good luck.

---

