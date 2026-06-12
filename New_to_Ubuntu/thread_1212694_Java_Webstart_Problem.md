---
title: "Java Webstart Problem"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by grivo242 on 2009-07-14
Hi all,

I'm having a problem with java webstart.  In 8.10, it would make a desktop icon when I downloaded a new application.  In 9.04, it doesn't do this any more.  I can run my application from the command line, but it has to re-download it every time.  I don't want to tax the server of my application like that.  Does anyone know how to get it to make a launcher on the deskptop again?

BTW, the app I'm trying to run is the CGoban client for KGS:

[http://www.gokgs.com/](http://www.gokgs.com/)

Thanks!

---

### Post by grivo242 on 2009-07-20
Replying to my own post:

I never figured out how to restore the function of Java Webstart where it created a desktop icon automatically, but I found that by creating a desktop launcher on my own with the command line worked pretty well, in my case:

javaws [http://files.gokgs.com/javaBin/cgoban.jnlp](http://files.gokgs.com/javaBin/cgoban.jnlp)


It doesn't seem to be downloading the program every time I launch it, and it starts right up pretty quickly.  The only downside is I don't have the correct icon for it.  :(

Hope this helps anyone with the same problem!

---

