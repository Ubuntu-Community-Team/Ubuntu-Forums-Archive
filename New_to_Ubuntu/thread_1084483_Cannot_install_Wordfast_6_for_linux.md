---
title: "Cannot install Wordfast 6 for linux"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by VojtaDziewiecki on 2009-03-02
I`m trying to install a CAT translation program Wordfast 6 on Xubuntu 
8.04.
It was written in Java and therefore should be platform-independent,
I`ve downloaded the "linux version" from this page:
[http://www.wordfast.com/store_download.html]("http://www.wordfast.com/store_download.html")
I unpacked it an double clicked the file Wordfast, which claims to be an executable, and it told me I needed Java so I installed sun java 6 from Synaptic. Double clicking does not work, when I typed ./Wordfast in the directory where I`ve unpacked it, the output was:
> vojta@vojta-desktop:~/install/Wordfast$ ./Wordfast 
2009-03-02 10:02:45,313 ERROR (main) [org.gs4tr.editor.commons.utils.LocaleUtils] - <Could not load exception locale list>

What am I doing wrong? How should I run applications like this one?

---

### Post by Sirron on 2009-03-02
This really depends on what the file you're trying to run is, please navigate to the directory you extracted to the file(s) to using "cd" in the terminal, then type "ls" and post the output.

As you probably know, that will return all the files in that directory including their extensions.

---

### Post by VojtaDziewiecki on 2009-03-02
OK Here`s the output:
> ls
configuration   features   plugins	       Wordfast
extensions      icon.xpm   product_licence.lic   workspace
file Wordfast 
Wordfast: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped


configuration, features, extensions, plugins and workspace are directories.

---

### Post by VojtaDziewiecki on 2009-03-02
Could it possibly be problem of my 64bit system?

---

### Post by gandaran on 2009-03-02
> **VojtaDziewiecki said:**
> Could it possibly be problem of my 64bit system?
could be, does that application run on 64-bits? you can also try remove the 32-bits synaptic sun-java and get the 64-bits java from sun java.com.
I tried it (32-bits system) works fine here just by double clicking the wordfast file.

---

### Post by VojtaDziewiecki on 2009-03-02
Well I made it work with wine. Maybe it`s not the best solution but it works.
Thanks for your help.

---

### Post by adm1968 on 2009-10-07
> **VojtaDziewiecki said:**
> Well I made it work with wine. Maybe it`s not the best solution but it works.
Thanks for your help.

No need to do that!
Try the other workaround (Sun's JRE for 64bits). Have you asked at proz.com (forums)?

Regards

---

