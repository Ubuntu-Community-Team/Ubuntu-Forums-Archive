---
title: "retrieve information from 2 files"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by subusona on 2009-05-19
SunOS UNIX
 
I have 2 files table_abc.txt and table_xyz.txt. Information as below need to be retrieved.
 
Thanks
 
table_abc.txt
---
sno   short_desc             flag
---------------------------------
1     hello                          Y
2     Good Morning             N
3     Good Evening             Y
4     Take Care                  Y
5     Good Bye                   N
6     WOW!                        Y

table_xyz.txt
---
Sno    logid 
------------
1      123
1      124
1      125
1      454
1      133
3      224
3      335
3      111
3      344
3      890
6      235
6      237

Unix Korn shell script should show
sno  count  Desc           flag
--------------------------------
1     5     hello                 Y
3     5     Good evening    Y
6     2     WOW!               Y

---

### Post by Titan8990 on 2009-05-19
A) sounds like homework
B) is not ubuntu
C) is not even BASH

---

### Post by subusona on 2009-05-19
Unix command to do this..... is my question not understandable??

---

### Post by ghostdog74 on 2009-05-19
if you are doing homework, put in more effort and show some code. If you are doing this for work, you should also prove your worth by showing what you have done.
```

awk 'FNR==NR {a[$1]++; next}
FNR>2{
  printf "%s %s ", $1,a[$1]
  for(i=2;i<=NF;i++){
   printf "%s " ,$i
  }
  print ""
}' secondfile firstfile


```

---

