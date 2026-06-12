---
title: "new on ubuntu and linux"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by bartgoris on 2010-01-15
Hello,
 
I'm a student physics and for this study, I have to use a linux program. I've chosen ubuntu because it looked the most simle (God, I was wrong...). After a long effort, I succeeded to instal gfortran and a c precompiler. :-)
 
Now, I had to download a file for the program I needed to use. Done this and put the file at Bart/DDA/SRC. Now the manual of the program tells me to position myself in the folder DDA/SRC and to type 'make DDSCAT'.
 
My question, how do I position myself to this folder, is it just opening it?
When I type 'make DDSCAT' in a terminal window, I get the response:
 
'Er is geen regel om doel DDSCAT te maken. Gestopt' 
Translated in English, this means
'There is no rule to create the target DDSCAT. Stopped'.
 
Can anybody help me?
thanks

---

### Post by marshmallow1304 on 2010-01-15
When you first open a terminal, you will be in /home/<username>

To see the contents of a directory, use
```
ls
```

To change directories, use
```
cd
```

In this case
```
cd DDA/SRC
```

---

### Post by arochester on 2010-01-15
Look at "How to install ANYTHING in Ubuntu!" at [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html) and "Installing Software in Ubuntu" on [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To compile in Ubuntu you first need to install the package: build-essentials

When you have decompressed the package you need to navigate, - move, into the new decompressed folder

---

### Post by bartgoris on 2010-01-15
Thank you very much (it worked)

---

### Post by Penguin Guy on 2010-01-15
> **bartgoris said:**
> Thank you very much (it worked)
I'm glad you found your answer. Please mark this topic as solved by clicking "Thread Tools" > "Mark as Solved". This helps other's with the same problem find a solution more easily. Thanks.

---

