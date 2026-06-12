---
title: "Compendium &amp; Mozilla Path"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2009-03-26
I've loaded a mindmap program "Compendium" into Ubuntu 8.10. It runs OK. But it should be able to start FireFox (I think) and connect ot the internet. The following is from the Progs readme:


QUOTE
Linux

Compendium is a Java application, so it requires a Java Runtime Environment (JRE 5.0+) to be installed before you can run it.

You can download this from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

Once you have downloaded the relevant .tar file from the compendiuminstitute.org website, simply unpack it.

You can run Compendium by navigating to the Compendium directory and typing: ./compendium.sh. I've done all this and it works.

TECH TIP: In order to automatically open external files and links on Linux, Compendium stores file extension and application associations in a file in <Compendium home folder>/System/resources called LaunchApplications.properties. This file is added to as the user tries to launch various file types for the first time and picks an application to use. We have preloaded this file with three type, 'www', 'http' and 'https', and we have associated them with the path '/usr/bin/mozilla'. If you do not have this application or have it in another location, you will need to edit this file appropriately.
END



The path quoted doesn't exit in my OS File System, it's obviously elsewhere. I would appreciate answers to the following:

1     I guess this path if present would start Firefox, Yes?
2     Then it would load the help file into Firefox, Yes?
3     How do I find the correct path?

Note I've searched the Compenduim forums without success.

---

### Post by yeats on 2009-03-26
You can always create a symbolic link to firefox:

```
cd /usr/bin
sudo ln -s firefox mozilla
```

You'll then have a file called /usr/bin/mozilla that points to firefox.

---

### Post by nicknefarious on 2010-01-02
I have downloaded and extracted this package Compendium 1.5.2 (and have JRE6 installed) but when I navigate to the directory and attempt to execute the command

```
./compendium.sh
```

it returns an error message saying "permission denied".

I also tried running it as root but get the same error.
Any ideas?

Thanks,

Nick

---

