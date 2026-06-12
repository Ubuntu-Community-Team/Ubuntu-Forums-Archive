---
title: "Installing Areca unable to find file with chmod"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-02-22
I was trying to install [Areca]("http://areca.sourceforge.net/documentation.php#tocHelp15") today (the files were in ./paulchinnz/download/areca) and ran this in terminal:

chmod a+x areca.sh check_version.sh

but got the reply that areca.sh couldn't be found. I then copied all the areca files into ./paulchinnz and this worked fine.

How could I have informed terminal where to look for areca.sh?

---

### Post by taurus on 2009-02-22
You either need to be in the directory where that file is or you have to include the whole path.

---

### Post by paulchinnz on 2009-02-22
Sorry taurus not sure about either of those two methods (I'm truly a beginner): I had the folder open, but clearly that doesn't constitute being 'in the directory', so what does; how do I include the whole path? Thanks.

---

### Post by quinnten83 on 2009-02-22
the entire filepath would be something like
/yourhomefolder/.paulchinnz/download/areca

so you could do a chmod like this chmod a+x /yourhomefolder/.paulchinnz/download/areca

or you would have to change into the directory
cd /homefolder./paulchinnz/download/areca
and then run chmod a+x areca

---

### Post by paulchinnz on 2009-02-23
Ah I see, thanks for that.

---

