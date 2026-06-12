---
title: "deletng filei"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by Drenriza on 2009-10-01
how do you delete a file from the command line called

tomme bla bla bla.ods

i have tryed rm \Time\rapport\support\Tommy.ods
but it just say

rm: kan ikke fjerne 'TimerapportsupportTommy.ods': No such file or directory
rm: cant remove 'TimerapportsupportTommy.ods': No such file or directory

i have also tryed as sudo. So what is going wrong.

Thanks on advance:KS

---

### Post by wojox on 2009-10-01
Try using forward slashes.

---

### Post by Drenriza on 2009-10-01
if i write the command without \ it says

Skrivebord$ rm Time rapport support Tommy.ods
rm: kan ikke fjerne 'Time': No such file or directory
rm: kan ikke fjerne 'rapport': No such file or directory
rm: kan ikke fjerne 'support': No such file or directory
rm: kan ikke fjerne 'Tommy.ods': No such file or directory

how do u remove a file with spaces in the file name.

---

### Post by Drenriza on 2009-10-01
if i write the file name with / forward slash it just says the same
No such file or directory

---

### Post by wojox on 2009-10-01
Sorry about that. I thought those were directories leading up to Tommy.ods

---

### Post by mimor on 2009-10-01
```
rm /Time/rapport/support/Tommy.ods
```

Yes, these are directory's (I guess), but this is not a windows machine ;)

---

### Post by 3rdalbum on 2009-10-01
If there are spaces in the filepath, you can do one of the following three things:

1. Put a backslash before every space ("escaping"):

/home/chris/letter\ to\ mum.odt

2. Enclose the whole path in quotes:

"/home/chris/letter to mum.odt"

3. Drag the file from your file browser onto the terminal window, which will fill in the path for you either with escaped spaces or quotes.

---

### Post by Drenriza on 2009-10-01
Thanks, by using "" to enclose the filename i could delete it :)

---

### Post by tom.swartz07 on 2009-10-01
> **Drenriza said:**
> Thanks, by using "" to enclose the filename i could delete it :)

dont forget to mark this as 'solved' under thread tools!
That way it could help other people easily find their answers!

Thanks!

---

### Post by linux-hack on 2009-10-01
if you have a file for example in /home/USER/myfile

if you want to delete the file you do :
```

rm /home/USER/myfile
```

and if it's a directory you do :

```
rm -R /home/USER/myfile
```

---

