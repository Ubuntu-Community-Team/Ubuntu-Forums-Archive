---
title: "Where do I find the .inf for my wireless card?"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by kngofqns on 2008-08-11
I installed the wireless driver from the website but it downloads as an .exe....I have the wrapper but I cant find the .inf

my card is bcm4318

---

### Post by chili555 on 2008-08-11
You need to extract the .inf with either cabextract, unshield, unzip or unrar. Just because your file is an .exe, doesn't mean it's not some other kind of file. If you do not have these installed on your system, then:```
sudo apt-get install cabextract unshield unzip unrar
```Then do:```
cabextract yourfile.exe
```If that doesnt work, try the others, unshield, unzip and unrar. Kepp going until you see the .inf file. Post back with details if you get stuck.

---

### Post by kngofqns on 2008-08-11
Will do thanks

---

### Post by wolfen69 on 2008-08-11
go [here]("http://biginoz.free.fr/linux/bcmwl5a.inf") and copy and paste whole page into text file and rename to bcmwl5.inf

---

### Post by kngofqns on 2008-08-11
what will i be doing with this?

---

### Post by kngofqns on 2008-08-11
this is what i get when i use unshield:

	unshield [-c COMPONENT] [-d DIRECTORY] [-D LEVEL] [-g GROUP] [-G] [-h] [-l] [-V] c|l|x CABFILE

Options:
	-c COMPONENT  Only list/extract this component
	-d DIRECTORY  Extract files to DIRECTORY
	-D LEVEL      Set debug log level
	                0 - No logging (default)
	                1 - Errors only
	                2 - Errors and warnings
	                3 - Errors, warnings and debug messages
	-g GROUP      Only list/extract this file group
	-h            Show this help message
	-j            Junk paths (do not make directories)
	-L            Make file and directory names lowercase
	-V            Print copyright and version information

Commands:
	c             List components
	g             List file groups
	l             List files
	t             Test files
	x             Extract files

Other:
	CABFILE       The file to list or extract contents of





not sure where to go from here

---

### Post by chili555 on 2008-08-11
> **kngofqns said:**
> what will i be doing with this?When you copy the text to a text editor, such as gedit or kwrite and rename it bcmwl5.inf, then that is the .inf file you need for ndiswrapper!> this is what i get when i use unshield:You might try unshield x yourfile.exe. As I said, it may not work and you may have to try the other methods.

---

### Post by kngofqns on 2008-08-11
alright i copied and pasted the text and saved it accordingly... but it says it is an invalid driver....any ideas?

---

