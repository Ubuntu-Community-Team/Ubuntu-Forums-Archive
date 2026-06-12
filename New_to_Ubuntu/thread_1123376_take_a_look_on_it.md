---
title: "take a look on it"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by shishir_knit on 2009-04-12
i m running this in terminal

$ ./copy.sh '/home/mine/Desktop/[B]my\ name/'
[/B]
and in shell script

[U]copy.sh
[/U]

echo $1>>test.txt
cp -a $1 /media/PENDRIVE

at place of** my name** if i give any name that has not got any space in it then the code is running

but for the above parameter its not working

and in test.txt also got the value

/home/mine/Desktop/my\ name/

so whats the error
can anybody help me through this

reply will be appreciated

---

### Post by Eisenwinter on 2009-04-12
./copy.sh "~/Desktop/my\ name/"

Try that.

---

