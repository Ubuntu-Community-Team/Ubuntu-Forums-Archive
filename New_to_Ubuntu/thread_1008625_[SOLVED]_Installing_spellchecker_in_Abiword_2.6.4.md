---
title: "[SOLVED] Installing spellchecker in Abiword 2.6.4"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by putanitsa on 2008-12-11
How would I install the French dictionary so that I can use the French spellchecker in Abiword?

I have downloaded and untarred the French canadian dictionary that I found [here]("http://www.abisource.com/download/abispell.phtml") and placed them in usr/share/abiword-2.6/dictionary, but it still returns "bonjour" as a spelling mistake...

I've looked in synaptic for a French aspell package but didn't find one.

What am I supposed to do? I'm using xubuntu if it makes any difference.

---

### Post by y6FgBn)~v on 2008-12-11
Just out of curiosity, did you select the language from Tools -> Set Language?

---

### Post by putanitsa on 2008-12-11
Yes, I set it to French (Canada), since that's what I (thought I) installed.

---

### Post by sneeks on 2008-12-11
if you go to synaptic package manager,and put abiword into search you will find all the add ons,and there is a lot !!!!!

---

### Post by putanitsa on 2008-12-11
The only results I get are:
abiword
abiword-help
abiword-plugin-mathview
abiword-plugin-grammar
abiword-plugins
abiword-common
libgtkmathview0c2a

... which are all installed and don't mention French...

What package should I even be looking for?

---

### Post by y6FgBn)~v on 2008-12-11
I followed your steps putanitsa and downloaded the french canadian dictionary and installed it in both the /usr/share/abiword-2.6 and also the /home/user/.AbiSuite. I also was unable to get a spelling correction on bonjour or bon jour. Unless someone else chimes in with a alternative I think you might have found a bug in the program.

Even a simple phrase like "Nous sommes ici" comes up as a misspelling. My french may be a bit rusty, its been awhile ;)

---

### Post by sneeks on 2008-12-11
> **sneeks said:**
> if you go to synaptic package manager,and put abiword into search you will find all the add ons,and there is a lot !!!!!

i just re-checked,and you are correct,im sure the last hardy i done had it there ,so will look further

---

### Post by putanitsa on 2008-12-11
**pcybill** Yes, my native inner French Canadian spellchecker confirms that "nous sommes ici" should show up as correct.

Well, other people seem to have had the same sort of difficulties. I've found some threads asking the same question, [without answers]("http://ubuntuforums.org/showthread.php?t=687039") or with [answers that might be outdated]("http://ubuntuforums.org/archive/index.php/t-129157.html"). I can't find any manual or help file dealing with this.

**sneeks** Just to clarify, I'm using Xubuntu Intrepid. Is that also what you're running?

---

### Post by putanitsa on 2008-12-12
I found a French aspell package [here]("http://packages.ubuntu.com/intrepid/aspell-fr"). Would installing it maybe enable a French spellchecker in Abiword, and if so, how do I install it? It doesn't include Canadian French, but that's ok. I'll just be happy to have *any* French dictionary working at this point.

---

### Post by putanitsa on 2008-12-12
Ok, so I went on a whim and typed "sudo apt-get install aspell-fr" and it worked. The spellchecker now works in French.

---

