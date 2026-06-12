---
title: "Choosing a language"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by gemm on 2009-06-04
Hello,

how can I change the languages in my system? I am using Ubuntu 8.10, and I have done until now the following:

In System --> Administration --> Language Support I have ticked the languages, which I want to use in "Supported Languages". 

In System --> Preferences --> Keyboard --> Layouts, under "Selected layouts", I have added the corresponding keyboard layouts for the languages, which I have selected. 

My problem is that I do not know how to enable the keyboard so that I can write in the language I want. In Windows I have a small icon on the panel which had the supported language, and I could choose the language from there. I could also do this with Ctrl+Shift. How can I do this in Ubuntu?
I have looked at System --> Preferences --> Keyboard shortcuts, but couldn't find any shortcut for this. And I also cannot find any icon for this.
Thanks a lot.

---

### Post by Mornedhel on 2009-06-04
Right click on Panel > Add to Panel... > Keyboard Indicator.

Alternatively, from console : setxkbmap [desired-language]

---

### Post by gemm on 2009-06-04
> **Mornedhel said:**
> Right click on Panel > Add to Panel... > Keyboard Indicator.

Alternatively, from console : setxkbmap [desired-language]

Thanks a lot! This is exactly what I needed.

---

