---
title: "bash: How to make LS (list directory) outputs like this ?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-05
first colum is name with fullfolderpath
second is file sizer (0 for folder)
then the date
then the time

how can bash ouptut this with sh or bash ?

```
/media/cdrom/file/folder/create/      0       2004.6.3        10:41.54
/media/cdrom/file/folder/create/TI-10_2.MAD     7169    2004.2.29       18:35.34
```


any help is very welcome will be very useful !

---

### Post by honeybear on 2010-10-05
```


[ -f "$i" ] && SIZEFF=` du -b -s "$i" | cut  -f1`
[ -d "$i" ] && SIZEFF=`stat --printf="%s" "$i"`  

DATECREATION=`date -r "$i" +%F,%H:%M`
DATECREATIONMOD=`date -r "$i" +%F | sed 's/-/./g'`
TIMECREATIONMOD=`date -r "$i"  +%H:%M.%S`

printf "$i\t$SIZEFF\t$DATECREATIONMOD\t$TIMECREATIONMOD" >>  $HOME/tmp/diskextendedlinuxlst  ; echo ""  >>  $HOME/tmp/diskextendedlinuxlst 




```

---

