---
title: "running multiple .deb files"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Gav1991 on 2010-12-21
How can i install all the .deb files in a directory with Terminal?

---

### Post by Verbeck on 2010-12-21
try *dpkg -i *.deb* from the folder

---

### Post by mcduck on 2010-12-21
make that *sudo dpkg -i *.deb* and you'll get the packages installed instead of an error about not having permissions.. ;)

---

### Post by Gav1991 on 2010-12-21
I don't want to install an individual file.

I want to install all of the .deb files in a directory with one command.

---

### Post by qamelian on 2010-12-21
> **Gav1991 said:**
> I don't want to install an individual file.

I want to install all of the .deb files in a directory with one command.
And that's what the above posters explined. By using * instead of the name of an individual deb file, you will be installing all of them.

---

### Post by Calash on 2010-12-21
> **Gav1991 said:**
> I don't want to install an individual file.

I want to install all of the .deb files in a directory with one command.

* is a wildcard and will fill in every item in the directory that ends with .deb so the commands posted "Should" work.

Have not tested it myself.

---

### Post by Verbeck on 2010-12-21
> **Gav1991 said:**
> I don't want to install an individual file.

I want to install all of the .deb files in a directory with one command.
thats what *sudo dpkg -i *****.deb *would do (thanx for the correction mcduck)
it'll configure all .deb files in the current directory 
else use  *sudo dpkg -i /path/to/folder/*.deb*

---

