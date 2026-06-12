---
title: "Awesome, I Compiled This Program! ...Now What?"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-09-16
Hey again, fellas.

I just compiled Musescore as per [these instructions]("http://www.musescore.org/en/handbook/compile-instructions-ubuntu") (since for some reason the most recent version of Musescore in Add/Remove is 4 versions old...) and everything seemed to go just fine...but I don't know what to do now.  How am I to install the program, or run it?

---

### Post by Ms_Angel_D on 2009-09-16
just guessing but try alt+f2 and then musescore

---

### Post by Wataru8675 on 2009-09-16
That runs the program that's 4 versions out of date. =/

It goes by "mscore" in the terminal, just for future reference in this thread.

---

### Post by mgranet on 2009-09-17
If you compile from source, using checkinstall will allow you to manage your compiled software from your package manager.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by Wataru8675 on 2009-09-17
God, maybe I'm dense, or maybe it's because it's late, but how do I run the program now that I've installed it with checkinstall?  I seemed to do it all right and got this:
```
 Done. The new package has been installed and saved to

 /home/kyle/mscore-0.9.3/mscore_0.9.3-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r mscore

```

Musescore is now gone from Applications > Sound & Video, and I can't run it from the terminal without it telling me to install it using apt-get install...wouldn't that just install the Musescore package that's 4 versions old?

I've also gone straight to the .deb package where it was installed with checkinstall and opened it with GDebi.  It says it was successfully REinstalled, but still nothing...

---

