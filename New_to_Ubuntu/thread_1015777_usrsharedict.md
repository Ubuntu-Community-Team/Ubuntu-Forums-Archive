---
title: "/usr/share/dict"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by caleb_yau on 2008-12-19
I was just doing some exploring and i noticed that in /usr/share/dict I only have 1 file called words. I typed $ file words and this popped up:

words: broken symbolic link to `/etc/dictionaries-common/words'

by default is this supposed to be the case, and if not how can i fix it?

Xubuntu Gutsy

---

### Post by mkvnmtr on 2008-12-19
I don't know if you have a problem but I found on my system a dict file up for auto-remove. To find out what it was I went to the package manager and put it in the search field.I found a lot of dictionary resources. When I had installed those I felt would be useful I had no auto -remove or broken packages. It might be you lack something to have the dictionary resources complete.

---

### Post by caleb_yau on 2008-12-19
ok new info. When I try to use aspell I get:
Error: No word lists can be found for the language "en_US".
How do i get dictionaries? And what is the canonical en_US dictionary?

---

### Post by caleb_yau on 2008-12-19
its cool, i just created my own words file from a random list of english words

---

### Post by decoherence on 2008-12-19
> **caleb_yau said:**
> its cool, i just created my own words file from a random list of english words

also try installing one of the word lists from synaptic. Just click the search button, make sure you're searching both name and description and search for /usr/share/dict

---

