---
title: "Gaming help"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by undying23 on 2009-05-09
I have the new Ubuntu; "Jaunty Jackalope" and I just installed Fable: The Lost Chapters through Wine, and extracted the .iso files as usual...when i attempted to play the game, i got an application error window, saying nothing but, "005D". I looked online and found that it was a problem with the DirectX9 files so i tried to reinstall them, when i did, i got an error saying, "DirectX did not copy a required file" so the installation failed. I'm unaware of what to do.

---

### Post by Temposs on 2009-05-09
It looks like there's a regression in the newer version of WINE that makes this game not work anymore. Check the comments here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3827](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3827)

Always check this page first for this game. It has the most up to date information. From what people are saying, you should install WINE version 1.1.10. I've found you a link to the deb installer for this version(i386 architecture):

[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.10~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.10~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

You can find other versions on this page in case that version doesn't work as well as you'd like:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Note that you most likely are running i386 architecture(most intel chips and 32-bit amd processors), but you should make sure you're not running amd64(64-bit amd processor) or lpia(applies to some netbooks) before running the installer I linked you to. The link above has each version for all three architectures.

---

