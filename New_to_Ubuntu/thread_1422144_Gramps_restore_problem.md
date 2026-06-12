---
title: "Gramps restore problem"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by asharpham on 2010-03-05
I had to reinstall Ubuntu on my drive so I saved everything I wanted. This included exporting my Gramps files which I saved to a usb stick. It was saved as a .gpkg file.

I've now redownloaded Gramps and want to restore my backup. But I can't import it. Gramps refuses to import it. Can anyone help me with this?

Alan.

---

### Post by coffeecat on 2010-03-05
I think the refusal of Gramps to import your .gpkg file is more to do with the odd way it has of setting up a database when Gramps is first installed. I've just successfully imported a .gpkg file to test this out and it worked. This is what you do:

First of all, backup anything you may have saved in Gramps since you reinstalled it, because you're going to delete the hidden folder that has all your personal Gramps settings and data. This is so we can start with a clean sheet. Close Gramps and open your home folder and click on View > Show Hidden Files. Locate the .gramps folder and delete it and all its contents. That's ".gramps" with a leading dot. Now reopen Gramps.

You'll get the main Gramps window and the Family Tree management window which is now empty. Click on "New" and you'll get "Family Tree 1". Rename it to what you want. **Before you close this window** click on "Load Family Tree". The Family Tree window will close and something seems to be loading in the main window, except that it will report Total people = 0. I think it's creating an empty skeleton database, because now if you click on the Family Trees menu, "import" is one of the choices and it should happily import your .gpkg file. It's when you omit to do the "Load Family Tree" bit that the Import option doesn't appear in the menu.

---

### Post by asharpham on 2010-03-05
I followed your instructions carefully but got this error message:
Media directory /home/alan/gramps-sharpham.gpkg.media exists. Delete it first then restart the import process.

I did a search for a .media file and found it. So I deleted it as required and then was able to import my backup. I have no idea where the .media file was but that's all that was stopping the import.

Thanks so much for your help.

Alan.

---

