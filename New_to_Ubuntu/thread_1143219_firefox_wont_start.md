---
title: "firefox wont start"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by aas452 on 2009-04-29
I am getting an error from the terminal when I try to start 

```

/usr/lib/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

Can anyone help?

---

### Post by MontelEdwards on 2009-04-29
> **aas452 said:**
> I am getting an error from the terminal when I try to start 

```

/usr/lib/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

Can anyone help?
hmm, i remember getting this error before.
I forgot what i did though.
I either reinstalled Firefox, or a simple restart fixed it.
I don't know

---

### Post by spiderbatdad on 2009-04-29
not entirely sure either, but you might check synaptic package manager for
libgtk-2.0-0, libgtk-bin, libgtk2.0-dev and the like.

---

### Post by aas452 on 2009-04-30
yeap they seem to be installed, I went ahead and reinstalled firefox but encounter the same error. hmmmm...

---

### Post by gandaran on 2009-04-30
rename the /home/user/.mozilla/ to .mozilla.old (backup) now restart firefox to see if it works, if it doesn't replace the the new .mozilla folder with the backup.

---

### Post by aas452 on 2009-04-30
same error, it seems like mozilla didnt even create a new .mozilla folder in home/usr/

---

