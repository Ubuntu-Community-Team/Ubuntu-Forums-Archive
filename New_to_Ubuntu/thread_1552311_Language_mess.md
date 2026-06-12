---
title: "Language mess"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by avanhel on 2010-08-13
At this moment I have a language problem with Ubuntu. I have selected English Great Britain as language at the login screen, but gnome and nautilus are in French, Firefox is in English, the terminal output is in german, and some parts also run in Dutch. 
I have installed the language packages for English, French, German and Dutch. 
I have tried to change something of the languages using the gnome-language-selector, but I have not succeeded. 
I have also tried to remove all the languages, this resets everything to English. But when I install the languages again they go back to the same weird mix. 
I looked in the /etc/enviroment file and into the /etc/default/locale file, but these files only contain the following:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_GB.utf8"
LANGUAGE="en_GB:en_US:fr_FR:de_DE:nl_NL:en"

Is there another file that I can edit to set the languages to the correct value?



I decided to reinstall Ubuntu to solve the problem

---

### Post by terdon on 2010-08-19
Wow... ok, thats weird. No idea whats going on but, why do you want all these language packs installed? If all you want is the ability to type in each of these languages then just install the keyboard layouts and not the language packs. 

I only have the english language pack installed but can type in english, spanish, french and greek by changing keyboard layouts. If you want your programs to be in another language then you should indeed install the different language packs. 

Also, have a look at .config/user-dirs.locale (just in case.

---

