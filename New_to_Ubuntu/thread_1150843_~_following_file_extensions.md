---
title: "~ following file extensions"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by jseth on 2009-05-06
I did an ls command on a directory, and noticed that all of my files have a ~ after the file extension, for example: Main.php~
This file is in addition to the "real" file, Main.php. When I open the Main.php~ in the browser, all of the code of the page displays. Of course I'd like to remove these files. Are they temp files? Does anyone know what is causing them and how to avoid them?
Thank you.

---

### Post by mcduck on 2009-05-06
They are backup files. Many programs default to saving the old version of a file as backup when saving changes to documents.

If you don't want them, you can usually disable that setting from the program's preferences. In your case you will most likely want to disable this in Gedit (the default text editor). To do that go to Edit/Preferences and on the Editor-tab disable "Create a backup copy of files before saving".

---

### Post by codysoyland on 2009-05-06
You can purge these files by running:
find . -name '*~' -exec rm '{}' \;

Be careful as this recursively looks through subdirectories.

---

