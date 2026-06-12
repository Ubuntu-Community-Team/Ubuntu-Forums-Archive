---
title: "can't extract a .rar file"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by dharanitharan on 2009-08-10
hi friends,
            is it possible to extract an .rar file in my ubuntu..:)

---

### Post by credobyte on 2009-08-10
In terminal:
```
sudo apt-get install unrar
```

Open your .rar archive with Archive Manager & extract wherever you need :)

---

### Post by jonathanysp on 2009-08-10
you might need to install the 'unrar' package. You can do that in the terminal with 'sudo apt-get install unrar' or through synaptic. Afterwards rar files should work!

---

### Post by dharanitharan on 2009-08-10
i had installed unrar ... even after that also i cant extract it...

---

### Post by mthalis on 2009-08-10
Are you sure you're file not corrupt? If not should work

---

### Post by Bradtek on 2009-08-10
Could be corrupt / incomplete .rar

You can definately extract .rar in Ubuntu
Right Click on file and select extract here
I don't even recall installing unrar

---

### Post by Arijit_Kundu on 2009-08-10
confirm that u have installed unrar, not only unrar free. also try to install xarchiver.

---

### Post by credobyte on 2009-08-10
Paste your archive into home directory and execute this command ( in case you get an error, post it here ):
```
cd $HOME && unrar x archive.rar
```

Open your home directory and it should be extracted :)

---

### Post by dharanitharan on 2009-08-10
my file s not corrupted... i can extract the same file in windows using winrar...

---

### Post by mthalis on 2009-08-10
What was your error message?

---

### Post by dharanitharan on 2009-08-11
in XArchiver i got this error message:

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/dharanitharan/Desktop/JAVA.rar

Extracting  JAVA/Pattern1.doc                                         Failed    
Extracting  JAVA/Pattern2.doc                                         Failed    
Extracting  JAVA/Pattern3.doc                                         Failed    
3 Failed

---

### Post by MidEvilHungarian on 2009-08-26
sudo apt-get install unrar-free 

worked for me.

---

### Post by leogagliardi on 2009-10-30
Unrar needs rar! 
I had the same problem and unrar do not advice you don`t have rar installed. 

Install rar:
/sudo apt-get install rar

Then try directly with unrar clicking on your compressed file.

If it doesn't work the other option is that your *.rar file was compressed with password. But, in that case the problem would be only with a specific .rar file
Saludos!

---

