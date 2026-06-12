---
title: "Spell Check not working in Open Office 3.0"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by hazypictures on 2009-10-04
I have been using Ubuntu 9.04 for 2 days. Open Office 3.0 is great except the spell check does not work in new and existing docs created in MS word.

I have read all three pages of this post and tried all the suggestions, but none have worked.  [http://ubuntuforums.org/showthread.php?t=204550&page=3](http://ubuntuforums.org/showthread.php?t=204550&page=3)


[LIST=1]
[*]I checked the settings in OO
[*]I used Terminal (although I'm not sure what I'm doing): sudo apt-get install myspell-en-ca. I get an error: "couldn't find package myspell-en-ca"
[*]I used Synaptic, and myspell-en-ca is not on the list (although the -us and -uk versions are both there...)
[/LIST]
Help. How can I install the Canadian dictionary and get it to work?

---

### Post by Daniel1994 on 2009-10-04
Hey and welcome!

I don't remember exactly what I did when I installed the norwegian dictionarys, but I can think of two things you should try:

1. Open synaptic(System>admin>Synaptic Package Manager) and search for openoffice. Scroll a bit down and you should see ALOT of dictionary packages. Click "Mark for installation" on the one you want, and press apply. Open Open Office and Tools>Settings>Language settings(or something, mine is norwegian)>Language and choose the desired language.

2. Go to [www.openoffice.org]("http://www.openoffice.org") and download and install your dictionary manually. Then open open office tools>language settings etc.

Good luck!

---

### Post by hazypictures on 2009-10-04
Thank you so much for your reply. When I tried this:

> **Daniel1994 said:**
> 
1. Open synaptic(System>admin>Synaptic Package Manager) and search for openoffice. Scroll a bit down and you should see ALOT of dictionary packages. Click "Mark for installation" on the one you want, and press apply. Open Open Office and Tools>Settings>Language settings(or something, mine is norwegian)>Language and choose the desired language.


I could not find System or Admin in Synaptic. I could see all the dictionaries, but not Canadian English. I tried to download US English and first it seemed to uninstall it, and then I installed it a 2nd time. But the spell check still does not work (I don't get an error message. It says that it has completed the check and found no errors, but I can see many errors.)

I also tried in OO to add a language (Tools -> Language -> More Dictionaries Online) and it takes me to this page: [http://extensions.services.openoffice.org/dictionary?cid=926385](http://extensions.services.openoffice.org/dictionary?cid=926385), which is a broken link.

In the Tools -> Language ->  Selection, there are a few language choices and there is a blue check next to Canadian English, but even if I select the text, it always says: "The spell check is complete".

I am stumped.

---

### Post by sandyd on 2009-10-04
Go to [http://extensions.services.openoffice.org/project/en_CA](http://extensions.services.openoffice.org/project/en_CA)

download the ditionary, then go to the extensions manager inside openoffice and install it.

EDIT: site is down. perhaps you can try tomorow.

---

### Post by Hagar Delest on 2009-10-05
Extension page works fine now.

I've added a special topic for 3.x spell checking management, it may help: [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512).

---

### Post by hazypictures on 2009-10-05
Thank you Carlee and Hagar de l'Est! I am spellchecking now.

---

### Post by originalmguy on 2009-11-04
> **carlee said:**
> Go to [http://extensions.services.openoffice.org/project/en_CA](http://extensions.services.openoffice.org/project/en_CA)

download the ditionary, then go to the extensions manager inside openoffice and install it.

EDIT: site is down. perhaps you can try tomorow.
Thanks for that! Worked pefectly! Thank God for the forums.
I really like the OS and OO but they have to correct this problem, or make more clear on how to install this feature. I know its free... but hey...

---

### Post by azitizz on 2009-11-04
Thank you! finally a simple solution that worked for me too!

---

