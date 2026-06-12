---
title: "How do I install this?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-27
There are things to download and unpack, but how do I install them and then launch them? (Hopefully from a GUI!)

---

### Post by Hamchan on 2009-04-27
If it's a .deb file, you just double click the icon

---

### Post by baizon on 2009-04-27
More information about the file extension please.

---

### Post by Paddy Landau on 2009-04-27
> **yeehi said:**
> There are things to download and unpack, but how do I install them and then launch them? (Hopefully from a GUI!)
It's impossible -- yes, literally -- for us to help you if you post such vague questions. Please be specific as to what you're trying to do, what you've tried, and what results you got.

---

### Post by eilios on 2009-04-27
You should be able to just launch the file by double clicking, if it's a source file you have to compile it (ugh). To compile(assuming it's in your documents)
```

cd ~/Documents
./configure
make
sudo make install

```

---

### Post by Cypher on 2009-04-27
What exactly is "this"???

---

### Post by theozzlives on 2009-04-27
You should stick with software in Synaptic or Add/Remove Programs. DEB files are easy also, but you sound to new to worry about anything else.

---

### Post by yeehi on 2009-04-27
:redface:

Haha! That was terrible! Sorry, I totally forgot to include the link to the file I am downloading. 

Here is the [page]("http://manpages.ubuntu.com/manpages/jaunty/man1/srm.1.html").

---

### Post by lukjad on 2009-04-27
Open the terminal (*Applications->Accessories->Terminal*) and type:

```
sudo apt-get install srm[TAB]
```

The tab should complete the command. If it doesn't, do TAB TAB and look at the list to decide which one you want.

---

### Post by brunogirin on 2009-04-27
You don't need to download and unpack anything, just install it though Synaptic.

[LIST]
[*]Go to System -> Administration -> Synaptic Package Manager
[*]Enter "secure-delete" in the search box, you should now see the secure-delete package at the top of the window
[*]Click on the checkbox next to the secure-delete package, a menu appears, select "Mark for installation"
[*]Click on the "Apply" icon (large green tick)
[/LIST]

---

### Post by oldos2er on 2009-04-27
Run
```
sudo apt-get install secure-delete
```
in a terminal.

---

