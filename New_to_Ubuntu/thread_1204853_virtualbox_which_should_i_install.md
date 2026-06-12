---
title: "virtualbox which should i install?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-05
there is a 2...something version on the repos to install
but i checked the official website and found a 3...something version and has an ubuntu(Jaunty Jackalope) package already build.
so which one should choose?

also whould i be able to try an os called beos through it?

---

### Post by xebian on 2009-07-05
> **heyyy said:**
> there is a 2...something version on the repos to install
but i checked the official website and found a 3...something version and has an ubuntu(Jaunty Jackalope) package already build.
so which one should choose?

also whould i be able to try an os called beos through it?

The debs direct from Vbox are better than from the repos. Especially if you need USB support which is not supported by the repo version

---

### Post by stwschool on 2009-07-05
Version 3 seems fine, and adds experimental DirectX support for Windows gamers. Beos I can't answer mind..

To get virtualbox and keep it fresh, go to System -> Administration -> Software Sources -> Add this...

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

Close and let it update, and v3 will appear in the repos :)

---

### Post by heyyy on 2009-07-05
> **stwschool said:**
> Version 3 seems fine, and adds experimental DirectX support for Windows gamers. Beos I can't answer mind..

To get virtualbox and keep it fresh, go to System -> Administration -> Software Sources -> Add this...

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

Close and let it update, and v3 will appear in the repos :)

is there a line for jaunty?(because on the downlaods section has a package ready for jaunty)
if i install from the site wont i have the "check for updates" box availiable?

---

