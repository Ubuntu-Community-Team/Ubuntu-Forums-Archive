---
title: "Adding IPA fonts"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by winjeel on 2009-07-18
I need to add IPA fonts so I can be sure that my already existing documents are compatible. I worry that saving in Linux Open Office may remove the fonts used in either Windows Word or Windows OO format.

The specific fonts I want to use (and have used) are from [this website]("http://www.phon.ucl.ac.uk/home/wells/fonts.htm"), and IPA fonts are used to communicate pronunciation, between phonologists, teachers, researchers, and even to students. How an American says "tomato" is different to how a Japanese or English person might say "tomato" (and you know that song), but these differences are not reflected in spelling, and adapting standard Roman Alphabet for pronunciation leads to a whole mess of problems. So, for research purposes, the IPA style is the style that must be used.

Question, where do I put these files (from the site linked above) and do I need to do any special way of installing them? (I've already downloaded the zipped file, and it's ready). And, I have used the Help and Search, already, but it didn't work (it just disappeared when I clicked on something).

Thanks in advance.

---

### Post by ronocdh on 2009-07-19
Easy! Whenever you need something, your first stop should also be Synaptic Package Manager. You can find almost *anything* in there, especially if you add extra repositories!

I tried searching for "IPA" and I found a package described as "Fonts suitable for education and institutional use"—not bad, eh? And it definitely has IPA!

You can get it yourself by typing this command into a terminal:```
sudo apt-get install tff-linex
```
Hope this helped!

---

