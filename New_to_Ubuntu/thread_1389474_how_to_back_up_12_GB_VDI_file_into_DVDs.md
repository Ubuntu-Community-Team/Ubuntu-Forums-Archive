---
title: "how to back up 12 GB VDI file into DVDs ?"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by medya on 2010-01-24
I have a 12GB VDI file (virtual disk) of virtualbox,

I wanna back it up in multiple DVDs in ubuntu 9.10, 

what do you suggest ?

---

### Post by hemimaniac on 2010-01-24
Personally I would rar/zip it up, then it can be broken into as many parts as you need (whether it will be going on 2 or 3 disks), archive manager or fileroller can handle this then just burn them.

---

### Post by mbzn on 2010-01-24
I believe tar has a function to split archives to a size limit

try 'man tar' 

Sorry about the lack of 'step by step' but i cant remember the correct arguments to do this

---

### Post by natravis on 2010-01-24
If you want a GUI answer, open Archive Manager (Applications -> Accessories -> Archive Manager). Create a new file, select where you would like to save it and open the bottom "arrow" to select split to volume of 4812 or less (that is about the max of DVD (you may want to make it 4800 just to give a little breathing room). You can also specify the file type if you would like but certain types have limitations on being split. I recommend .7z personally, but I'm sure others will have an opinion

---

### Post by HermanAB on 2010-01-24
The CGI way is with 'split' and 'cat'.

---

### Post by medya on 2010-01-24
> **HermanAB said:**
> The CGI way is with 'split' and 'cat'.

whats CGI way

---

### Post by natravis on 2010-01-25
> **medya said:**
> whats CGI way

I think he meant CLI for command line interface. Just run the GUI method I stated. Easier than explaining the intricacies of the the CLI stuff. If you want to investigate that, type man tar, man cat, or man whatever command you want to find out the usage. If this answers your question, make sure you mark the thread as solved.

---

