---
title: "batch processing"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by jrev on 2010-12-18
Hello,

I have on a USB key a number of files to convert to read/write permission.

I do for each file > chmod 777 file_name

How can I process all files in one command ?

Hope you get my point 
Thanks

---

### Post by Verbeck on 2010-12-18
just use recursive
```

chmod **-R** 777 /directory/name
```

---

### Post by jrev on 2010-12-18
As I cannot name all folders I had to type > # chmod -Rv 777 /directory/*

Thanks for your answer

---

