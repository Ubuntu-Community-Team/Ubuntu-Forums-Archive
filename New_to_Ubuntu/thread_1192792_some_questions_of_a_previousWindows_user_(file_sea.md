---
title: "some questions of a previousWindows user (file search, context menu etc)"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by melolontha-melolontha on 2009-06-20
1.) When I do a search in the UBUNTU equivalent of Exporer (file browser), I get a results list. Example: somehow, I lost the associations for Evolution and I want to recover them, so I search on the whole computer for "Evolution". One of the many results is the mail program, if I double click on it, it opens and I can use it. But how do I find out the actual position of the search-result? In Windows, I would right click on it and I would find something like "create shortcut". Also there, the file browser has an options of "address in the title bar" or "address in the address bar", so one easily can extract the path to a file or folder, copy and pasten it for other purposes and the like. - In order to reestablish the association from the launch bar I have to enter the comlete path to the evolution executable.

Some friend has once made me something to extend the context menu of Windows' Explorer to copy the UNC Path to any resource (be it on my computer or one connected through the network) to the clipboard. Then I might paste this e.g. to an email telling someone: look here xxxx and xxxx would appear blue and underlined as a link. (Due to some strange thing in MS, you need two variants of the UNC Path: one for mail and another variant for creating shortcuts/links).

2.) I was told that almost all programs under UBUNTU can be run from a terminal and many of them can even be told to do the right thing by adding the right command line paraameters. But how do I find out the name of a GUI programs, in order to ask for available command line arguments by progname --help

3.) how can I create a link to a file with the above mentioned file browser (If I had the answer to question 2, I knew its name)?

4.)Is the UBUNTU clipboard limited to text only (formatted or unformatted)? Does one need an extension to be able to cut and paste images from one application to another?

5.) In DOS and Windows, files are distinguished by type by the file name extension. (I know thah one can disguise something by deliberately giving a file a wrong extension and this may even be misued to wreck ones system). In UBUNTU, I found some file extensions associated with OpenOffice, some .tar.gz and so on which are compressed archives. I would like to know a list of the most important file extensions used on UBUNTU systems.

Kind regards and thanks for these absolute beginner questions!

---

### Post by arikshtiv on 2009-06-20
4. The clipboard is not limited as far as I know, you can even copy and paste images from paint(under wine) to gimp.

---

### Post by krzysz00 on 2009-06-20
linux files usually don't NEED an extension, sometimes one is used to indicate the type of file (.so == shared object (for example))

---

### Post by krzysz00 on 2009-06-20
Oh. System->Preferences->Main Menu->(program in question (find in dialog)) Select, hit properties, a path is there. Anything of the form /blah/name or /blah/blah/name is a full path. Take everything before the last / out and the name of the program is there (don't worry, sometimes just "name" is given) Also remember a sudo (if any)

---

### Post by juancarlospaco on 2009-06-20
> **melolontha-melolontha said:**
> 1.) When I do a search in the UBUNTU equivalent of Exporer (file browser), I get a results list. Example: somehow, I lost the associations for Evolution and I want to recover them, so I search on the whole computer for "Evolution". One of the many results is the mail program, if I double click on it, it opens and I can use it. But how do I find out the actual position of the search-result? In Windows, I would right click on it and I would find something like "create shortcut". Also there, the file browser has an options of "address in the title bar" or "address in the address bar", so one easily can extract the path to a file or folder, copy and pasten it for other purposes and the like. - In order to reestablish the association from the launch bar I have to enter the comlete path to the evolution executable.

On Linux does'nt matter the actual position, it can be launched from everywhere.
Just make a launcher calling *" evolution "* and its done.

The* "address bar"* has a little button on the left side, click it, 
its change **[path] [to] [somewhere]** to **/path/to/somewhere/**


> **melolontha-melolontha said:**
> 2.) I was told that almost all programs under UBUNTU can be run from a terminal and many of them can even be told to do the right thing by adding the right command line paraameters. But how do I find out the name of a GUI programs, in order to ask for available command line arguments by progname --help 

type the first letters on the terminal and press TAB twice,
example:

nau
TAB TAB
nautilus

> **melolontha-melolontha said:**
> 3.) how can I create a link to a file with the above mentioned file browser (If I had the answer to question 2, I knew its name)?

a Launcher containing:
**nautilus link/to/a/file**

> **melolontha-melolontha said:**
> 4.)Is the UBUNTU clipboard limited to text only (formatted or unformatted)? Does one need an extension to be able to cut and paste images from one application to another?

No, its not limited to text only.
Try Drag&Drop works nice too.

> **melolontha-melolontha said:**
> 5.) In DOS and Windows, files are distinguished by type by the file name extension. (I know thah one can disguise something by deliberately giving a file a wrong extension and this may even be misued to wreck ones system). In UBUNTU, I found some file extensions associated with OpenOffice, some .tar.gz and so on which are compressed archives. I would like to know a list of the most important file extensions used on UBUNTU systems.

on Terminal type and press enter:
file file
example:
file MyDocument.odt
file MyMSDoc.doc

On Linux does'nt matter the file extension.

---

