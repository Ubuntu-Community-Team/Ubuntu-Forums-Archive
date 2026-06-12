---
title: "trouble with an install file"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by spacedninja on 2011-06-21
so i've compiled from the tgz and made the install file however now i'm having a new issue.
when i try and install it asks for root permission so i give it. then it says that 
"/home/desktop/454//home/desktop/454" is an invalid file which it is. i don't know why its trying to go to the file all over again from the original location. any suggestions?

---

### Post by ruffEdgz on 2011-06-21
Are you doing this through the terminal and if you are, what command are you trying to run?

If you can give use some more information like the steps you are taking to get this tar file uncompressed, that would help.

Cheers!

---

### Post by spacedninja on 2011-06-21
I used the gui to unpack it, it came with the install file, so I ran that in the terminal, it gave me the choice to install it as either root or sudo, I picked root, then it gave the error right after I entered the password.

"bash: /home/john/Desktop/454/DataAnalysis_2.3//home/john/Desktop/454/DataAnalysis_2.3/INSTALL: No such file or directory"

---

### Post by spacedninja on 2011-06-21
Figured it out. feel reeeeeeeeal dumb right about now. 
fix was as simple as opening the terminal in the directory that had the install file as root and typing: bash INSTALL

thanks for your time though. im serious about that.

-space

---

### Post by dFlyer on 2011-06-21
Please mark as SOLVED.

---

