---
title: "run .bin file"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by ubudog on 2009-02-08
How do I run a .bin file?

---

### Post by photon_man62 on 2009-02-08
Right-Click on it, go to Properties, go to the Permissions tab and check "Allow executing file as program" or something like that.

---

### Post by ptn107 on 2009-02-08
Right-click the file, select properties from the context menu, click the permissions tab, check the box next to 'Allow executing file as program'.  Click ok.  Now double-click the file and press 'Run in terminal'.

---

### Post by ubudog on 2009-02-08
I did that and it says there is no application installed to run this type of file.

---

### Post by photon_man62 on 2009-02-08
> **ubudog said:**
> I did that and it says there is no application installed to run this type of file.

In that case try running it in the terminal.

---

### Post by howefield on 2009-02-08
What's the name of the file and where did you get it from ?

---

### Post by tehforum on 2009-02-08
1) Download the .bin file

2) Open up the Terminal (Applications > Accessories > Terminal).

3) In the terminal, type in "cd Desktop" (without the quotes) then press enter

4) Type "ls" (without quotes) in the terminal, then press enter. This will list all the files on your desktop

5) Type "sudo chmod +x filename.bin" (without the quotes). Replace filename.bin with the name of your .bin file.

6) You may be prompted to type in your login password, do so, then press "Enter"

7) Now type "./filename.bin" (without the quotes). Replace filename.bin with the name of your .bin file. Then press "Enter". Now the installation of the .bin file will begin.

Hope it helps. :D

---

### Post by ibuclaw on 2009-02-08
To execute a .bin file, open a terminal and **cd** to the directory that contains the file, then type in
```
./**name-of-file**.bin
```

But more to the point ....

What is the name of the file, where did you get it from ?

Security is a big big thing in Linux, and we wouldn't want you running anything that we may consider to be malicious to your computer :)

Regards
Iain

---

### Post by taurus on 2009-02-08
> **tehforum said:**
> 
5) Type "**sudo** chmod +x filename.bin" (without the quotes). Replace filename.bin with the name of your .bin file.

7) Now type "./filename.bin" (without the quotes). Replace filename.bin with the name of your .bin file. Then press "Enter". Now the installation of the .bin file will begin.


You don't have to include the sudo if you want to change the permission of that file since you are the owner of it.  

However, you might need to add sudo in front of the ./filename.bin if it's trying to install to the system.

---

### Post by ubudog on 2009-02-08
How do I run it in a terminal.  The window doesn't come up to select "run in terminal."

---

### Post by tehforum on 2009-02-08
[http://ubuntuforums.org/showpost.php?p=6699494&postcount=7](http://ubuntuforums.org/showpost.php?p=6699494&postcount=7)

There.

---

### Post by ubudog on 2009-02-08
> **tehforum said:**
> 1) Download the .bin file

2) Open up the Terminal (Applications > Accessories > Terminal).

3) In the terminal, type in "cd Desktop" (without the quotes) then press enter

4) Type "ls" (without quotes) in the terminal, then press enter. This will list all the files on your desktop

5) Type "sudo chmod +x filename.bin" (without the quotes). Replace filename.bin with the name of your .bin file.

6) You may be prompted to type in your login password, do so, then press "Enter"

7) Now type "./filename.bin" (without the quotes). Replace filename.bin with the name of your .bin file. Then press "Enter". Now the installation of the .bin file will begin.

Hope it helps. :D

Thanks that worked! Security is not a big big issue in linux?!

---

### Post by tehforum on 2009-02-08
No problem. Glad it worked!

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) - More on security.

---

### Post by ubudog on 2009-02-08
Thanks so much!!

---

### Post by ibuclaw on 2009-02-08
> **ubudog said:**
> Thanks that worked! Security is not a big big issue in linux?!

That is not what I was saying.

Though you are very secure and can be rest assured that Ubuntu will probably never get any viruses/spyware whilst you are running it.

That does not mean to say that you can't do other disastrous things to your computer. And it also does not mean that you can take a relaxed stance on security or the implications of what you are doing when you are running downloaded executables/installer files.

The majority of web Servers on the internet run on *NIX based machines, so there is no lack of motivation to hack into your computer, and a malicious binary blob could be the trigger of the cause of that, if it were to happen. :)

But enough of the pep talk. I'll just assume that you know what you are doing.

Regards
Iain

---

### Post by ubudog on 2009-02-08
Oh, I see what you meant.

---

