---
title: "problem with mv command"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-22
i just wanted to move a file from one directory to another 
i typed this command 
the file name is add.deb
sudo mv add.deb /ubuntu
but there is no folder named ubuntu in that directory(i forgot)
but the file is missing
help thanks in advance

---

### Post by Kareeser on 2009-02-22
Your file "add.deb" has been renamed "ubuntu" and is now placed in the root of the drive, "/"

```
sudo mv /ubuntu ~/Desktop/add.deb
```

That should fix it :)

---

### Post by gkraju on 2009-02-22
> **Kareeser said:**
> Your file "add.deb" has been renamed "ubuntu" and is now placed in the root of the drive, "/"

```
sudo mv /ubuntu ~/Desktop/add.deb
```

That should fix it :)


it doesnt worked it showed 
mv: cannot stat `/ubuntu': No such file or directory

---

### Post by mamut0o1 on 2009-02-22
> **gkraju said:**
> it doesnt worked it showed 
mv: cannot stat `/ubuntu': No such file or directory

go to the main directory:  cd /
then type ls to view all files

do you see the file name there?
linux files are case sensitive as well so make sure you type the file name correctly.

---

### Post by ajgreeny on 2009-02-22
> sudo mv /ubuntu ~/Desktop/add.deb That should fix it :smile: 			 		 	 	 
it doesnt worked it showed 
mv: cannot stat `/ubuntu': No such file or directoryIt look like you added a space after the / in /ubuntu.  Remove it and try again.

---

