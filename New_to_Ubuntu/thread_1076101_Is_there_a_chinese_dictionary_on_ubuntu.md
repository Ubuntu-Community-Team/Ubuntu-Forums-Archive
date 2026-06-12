---
title: "Is there a chinese dictionary on ubuntu?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-02-21
i was just wondering if there is a chinese dictionary on ubuntu?

I have found Kiten which is an English to Japanese and Japanese to English dictionary. Which is quite excellent, even great for offline too. (since i don't have an internet connection at home)

Does anyone know where can I get one, that I can install and not have to go online to use search for each individual chinese character?

I am looking for traditional character btw.

your input will be greatly appreciated

---

### Post by ramjet_1953 on 2009-02-21
This link may be of use:

[http://packages.ubuntu.com/gutsy/dict-xdict](http://packages.ubuntu.com/gutsy/dict-xdict)

Regards,
Roger:D

---

### Post by shiningkenmonster on 2009-02-22
okay, this doesn't help me much. Does anyone else have anything to say? Still need a chinese dictionary

---

### Post by raydeen on 2009-02-22
Go to Administration/Synaptic Package Manager and select and install the following:

opendict     (dictionary client)
dict
dictd        (dictionary server)
dict-xdict   (English/Chinese dictionary)

There will be some other things that will get installed, but you'll then get the program OpenDict under Accessories once all has been installed. You can then select the English to Chinese dictionary and search some words. The Chinese output is in Chinese characters, not phonetic English so you'll have to be able to read Chinese.

---

### Post by llamabr on 2009-02-22
How about any of these:

brock@vader:~$ apt-cache search chinese dictionary
dict-stardic - An English to Chinese Dictionary
dict-xdict - An English to Chinese Dictionary
hanzim - Chinese character learning aid
stardic - an English-Chinese dictionary software for Unix
brock@vader:~$

---

