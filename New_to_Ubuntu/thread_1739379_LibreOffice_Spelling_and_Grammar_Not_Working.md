---
title: "LibreOffice Spelling and Grammar Not Working"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by garl on 2011-04-25
I'm new to Linux and Ubuntu (this is my second day), and my friend recommended using LibreOffice over OpenOffice since Oracle is garbage; his words, not mine. (:  I used the terminal and entered:

sudo apt-get remove openoffice*.*

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
sudo apt-get install libreoffice-gnome

I noticed that the Spelling and Grammar check in LibreOffice Writer isn't working. It says spellcheck complete without finding any errors. I assume I need to install a dictionary add-on or something? Any help would be appreciated!

---

### Post by bioterror on 2011-04-25
install aspell, hunspell or what ever there's.
Choose your favourite weapon of spell checking.

---

### Post by garl on 2011-04-25
Have hunspell working now. Merci beaucoup! <3

---

### Post by HDave on 2011-07-08
A simple
```

sudo aptitude install hunspell
```

work for me too.  Thanks.

---

### Post by ervinodsingh on 2012-10-16
spelling check worked but not grammar check.

---

