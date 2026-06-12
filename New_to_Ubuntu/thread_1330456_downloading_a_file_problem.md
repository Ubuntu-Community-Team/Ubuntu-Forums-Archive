---
title: "downloading a file problem"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by portset on 2009-11-18
[FONT=Courier New]Can anyone advise what is wrong with this call in 8.04 please.[/FONT]
[FONT=Courier New]$ curl [/FONT][[FONT=Courier New][COLOR=#444444]http://android.git.kernel.org/repo[/COLOR][/FONT]]("http://android.git.kernel.org/repo")[FONT=Courier New] >~/bin/repo[/FONT]

---

### Post by Baelus on 2009-11-18
Try this:

```
wget -P ~/bin http://android.git.kernel.org/repo
```

---

