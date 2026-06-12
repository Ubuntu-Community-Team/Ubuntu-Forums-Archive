---
title: "Disable unused regional language variants in spelling checker"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by RRoel on 2011-04-06
When I switch my spelling checker in Geany, Firefox, Thunderbird etc. between languages (UK/US English, NL Dutch, DE German, ES Spanish) I have to plough through an impressive list of all thinkable regional variants of these languages. Is there a way of removing these variants from these menus?

One more related question: what is the best choice for Oxford spelling (-ize, -yse, -our etc.) for those special moments you just feel like using it? Would that be Canadian English or is there a better way?

---

### Post by RRoel on 2011-04-20
BUMP!

Am I the only one who changes between different languages in the spelling checker?
Or did I post in the wrong place?
please let me know!

It bothers me most in Firefox, where all languages seem to be in a random order.
But also Geany and Thunderbird would be more convenient if I could disable those 90% I don't use anyway...

---

### Post by vangelas on 2011-09-05
Go to synaptic, search for English and remove all variants you don't need. That removed all the English language variants, but I wasn't able to remove variants of my second language...yet. Hope this helps!

---

### Post by JRV on 2011-09-05
Try localepurge, it removes all the languages you do not want.

Install it with the command
```
sudo apt-get install localepurge
```

During the install process you are asked to check the languages you want to **keep**.  All others will be **deleted**.

Then run the program with the command
```
localepurge
```

One drawback of the localepurge command, it is slow.  It will automatically be executed at the end of every update, and any time you install a program.  It will sometimes run multiple times.

The language packs you choose to keep are stored in /etc/locale.nopurge

---

### Post by Francois_C on 2012-10-11
Thanks, especially for localepurge, which is a bliss!
The ideology of Open Source Software has some connections with conventional self-righteousness, ecology and many modern trends that defend minorities, endangered species, think that small things deserve as much respect as the great and so on. These are good things in theory, but it leads to intellectual short-sightness and sometimes stupidity, as large = small, futile = important, etc.
For instance the installer of LibreOffice Windows installs by default on a French system the Zulu spell-checker and even spell-checkers of languages I never heard of before (I'm a retired Literature teacher, though).
As concerns Firefox, the Synaptic trick seems to work, but, even using both tips I was unable of removing all variants of English: we French are forced to use English nearly everywhere - instead of our cherished Molière's language - but we don't care for nuances. US-English is good enough for us. Pidgin would be sufficient; but it seems my coarse English is detected as Australian. Sorry for the Australian...

---

### Post by Francois_C on 2012-12-22
[Two months later] I have just found the way to get rid of those language variants in Firefox: I went to /usr/share/hunspell in root mode with Gnome Commander, and deleted all EN_AU, EN_GB, EN_ZA files, and also symlinks to fr_ca, fr_ch, fr_lu, fr_mc that were there.
I should also have deleted the files which the links were pointing to: The Belgian, Swiss, Luxembourgian, write the same French as us (sometimes just a little better! and my own French is far closer to Belgium than Southern France) except for the way they say 70 and 90 (plus 80 for the Swiss).
But the mean absurdity and vain work was a special dictionary for Monaco, a 2 km2 (0.77 square miles!) state, with less than 20,000 inhabitants, including French tax evaders!

---

