---
title: "Dictionary in abiword"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-04-19
How do I install dictionaries in abiword? All I can find are .exe files for Windows.

---

### Post by ashmew2 on 2009-04-19
Hi there , I think you should take a look here : [http://www.abisource.com/download/abispell.phtml](http://www.abisource.com/download/abispell.phtml)

I think that must be what you're looking for. Correct me im wrong though ;)

---

### Post by llamabr on 2009-04-19
What types of dictionaries?  Different languages?

---

### Post by Mr.Kuchinawa on 2009-04-19
I.. don't know. All I can see is rpm, zip and tar. I would guess the tar's are for me, but I have no idea of how to install them. Could this be done via synaptic? I'm completely lost here.

---

### Post by llamabr on 2009-04-19
Uh, huh.  What type of dictionaries do you want?  You want to add new languages?  Or is there some problem with the dictionary that came with it?

---

### Post by mprince on 2009-04-19
If you are trying to add a spell check dictionary, then open a terminal and type:

```
sudo apt-get install aspell-en
```



You may also need to type this to get it to work:

```
sudo apt-get install aspell-doc

sudo apt-get install spellutils
```

---

### Post by Mr.Kuchinawa on 2009-04-19
I don't think that worked. At least not very well. In english, It claims that some common word are written wrong (like "we")

---

### Post by mprince on 2009-04-21
This thread might be what you need:

[http://ubuntuforums.org/showthread.php?t=129157](http://ubuntuforums.org/showthread.php?t=129157)

---

### Post by Merlin2007 on 2011-01-06
I posted a solution for Ubuntu 10.10
Search for
**How to install Aspell Language Dictionaries for Abiword in Ubuntu 10.10  **

---

