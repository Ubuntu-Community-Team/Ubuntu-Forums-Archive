---
title: "Change Encoding of a Text File"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-08-10
Hi, 
I've a text file with an unknown encoding(probably Arabic) and I want to change it to UTF-8; how can I do that in Ubuntu?
Thanks.

---

### Post by arky on 2009-08-10
Open the file in Gedit and select 'Save As' from the file menu. You can save it in different character encoding from 'Character Coding' menu.

---

### Post by Hoom@n on 2009-08-10
> **arky said:**
> Open the file in Gedit and select 'Save As' from the file menu. You can save it in different character encoding from 'Character Coding' menu.
Thanks, but I don't want that. I want to reload the text file in a new encoding. e.g. I have "ÇÒ Ý&#732;Ñã ÈíÑæä äãíÑÝÊ" now, which should be something like "&#1740;&#1608;&#1606;&#1740;&#1705;&#1583; &#1578;&#1587;&#1578;" and "ÇÒ Ý&#732;Ñã ÈíÑæä äãíÑÝÊ" won't change to a readable thing by saving as.

---

### Post by Mornedhel on 2009-08-10
If you knew the original encoding, you could use ```
iconv -f ORIGINALENCODING -t utf-8 ORIGINALFILE > TARGETFILE
```

You can try and detect the encoding with ```
file YOURFILE
```

The detection doesn't always work as it relies on some inaccurate magicks, but it does work most of the time.

---

### Post by tatojo on 2012-05-19
iconv -f  worked for me. I just change a file in ISO-8859-1 to utf-8.
Of course, I found the enconding with file, as you suggest.
Thank you.

---

