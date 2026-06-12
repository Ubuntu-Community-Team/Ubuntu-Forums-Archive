---
title: "Windows Viruses"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by shoaibi on 2009-09-09
I copied some data from here and there on my jaunty and now i find some many eml and HTML:Nimda viruses on my system when i scan it using clamtk. Problem is that these are 1700+ files that i have to manually select and do action. Plus clamtk doesnt clean it? is there any other way possible to remove thesem viruses?


[EDIT]
I have a finding to share, all infected html files contain:
```

<html><script language="JavaScript">window.open("readme.eml", null,"resizable=no,top=6000,left=6000")</script></html>

```

so all i gotta do is:

1. Search for all eml files, delete them.
2. Search for all html files, grep them for these lines, if the lines exists, i would have to delete any lines that match the pattern of :
<html><script language="JavaScript">window.open("readme.eml", null,

I think i need a script, my own scripting isnt really great but i will try, in a mean while i am waiting here for answers.

---

### Post by credobyte on 2009-09-09
Wouldn't it be easier to remove all .eml files ?

```
locate readme.eml
```

---

### Post by shoaibi on 2009-09-09
thanks, i made:
```

locate "*.eml" | while IFS= read -r line; do echo FOUND: $line; done
for file in $(find / -type f -name '*.html' -print); do     echo Looking at $file;     sed -ie '/readme.eml/d'   $file; done

```

have added it to "at" 00:00.

[EDIT]:
I end up with:

```

echo UPDATING DB
updatedb
echo """



"""
echo LOCATING FILES AND DELETING EML VIRUSES
locate "*.eml" | while IFS= read -r line; do echo FOUND: $line;rm -vf $line; done
echo """



"""
echo DELETING HTML VIRUSES

for file (**/*.html);do echo Looking at $file;     sed -e '/readme.eml/d' <(<$file) > $file; done
#for file in $(find / -type f -name '*.html' -print); do     echo Looking at $file;     sed -ie '/readme.eml/d'   $file; done
echo """




"""
echo DONE

```

---

