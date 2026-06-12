---
title: "Text all in Greek with us locales"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Gidskid on 2009-05-07
I have recently Upgraded to Jaunty 9.04. All is good until one day, i fire up LMMS and i can't read the text because it's in a Greek Handwriting style. This is very strange. I open Open office and that too has Greek Handwriting. Most of my Other applications, such as Pidgin, Firefox and Mixxx are all perfectly Legible. I honestly don't know what to do about it. I have been into my Settings and Found that my Fonts are all set to defaults.

Please Help

G

---

### Post by Temposs on 2009-05-07
Go to System->Preferences->Appearance->Fonts, and check what is set there. I'll bet your "Document Font" is set to something weird :-)

---

### Post by raymondh on 2009-05-07
> **temposs said:**
> go to system->preferences->appearance->fonts, and check what is set there. I'll bet your "document font" is set to something weird :-)

+1

---

### Post by Gidskid on 2009-05-08
No my Document font was set to Sans. This I don't think its actually "Font Related", I would try and change it in the actual Program settings, unfortunately I can't read them!

---

### Post by arashiko28 on 2009-05-08
Go to system, administration and choose language support. That would be, the next words:

> 	&#963;&#973;&#963;&#964;&#951;&#956;&#945; > &#948;&#953;&#959;&#943;&#954;&#951;&#963;&#951; > &#947;&#955;&#969;&#963;&#963;&#953;&#954;&#942; &#965;&#960;&#959;&#963;&#964;&#942;&#961;&#953;&#958;&#951;

then you will have a box with two language options, the first one for menus and windows, and the second one for everyone at startup to see, on both go for:
> 	
&#913;&#947;&#947;&#955;&#953;&#954;&#940; (&#919;&#957;&#969;&#956;&#941;&#957;&#949;&#962; &#928;&#959;&#955;&#953;&#964;&#949;&#943;&#949;&#962;) That is English, United States. I think that should solve your problem if it's truly in Greek.

---

### Post by Psychopump on 2009-05-08
> **arashiko28 said:**
> Go to system, administration and choose language support. That would be, the next words:



then you will have a box with two language options, the first one for menus and windows, and the second one for everyone at startup to see, on both go for:
 That is English, United States. I think that should solve your problem if it's truly in Greek.

Wow, that is some concise advice! Well done!

---

### Post by Gidskid on 2009-05-12
this didn't work as the only languages installed are English US and English UK.

Any more help please?

---

### Post by bapoumba on 2009-05-12
I have edited your title to something more relevant :)

Just to make sure, please open a terminal and paste the output to:
```
locale
```

Could it be the theme you are using? Do you remember if you installed something before it happened?

---

### Post by Gidskid on 2009-05-12
Ok as you requested, here it is.

LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=


Sorry this would be in a little box, however I don't know which button to use.

---

### Post by zero7404 on 2009-05-12
is it necessary to add Greek as a locale or install it from synaptic if I wish to use that language to type text ? i'd like to have it so that i can switch between english/greek keyboard layout.

the language i used to install ubuntu is english.

---

### Post by Gidskid on 2009-05-12
Dude its just a pain 'cos you can't read anything. I seriously wouldn't go near it with a forty foot pole if I were you!

---

### Post by zero7404 on 2009-05-12
> **Gidskid said:**
> Dude its just a pain 'cos you can't read anything. I seriously wouldn't go near it with a forty foot pole if I were you!

you're mistaken, i can read it.

---

### Post by Gidskid on 2009-05-13
Oh sorry, I can't read it because I am not Greek. Also it's not actually in Greek, it's just the font.

---

### Post by unutbu on 2009-05-13
Gidskid, I'm guessing that the problem lies in a GNOME configuration file in your home directory -- that it is not a system-wide problem.

All GNOME configuration files (that I know about) are in one of the following directories: .gconf, .gnome2 or .config.

So perhaps try the following: rename each of these directories to something else. For example, rename .gconf --> .gconf-old.

Then log out, and log back in. GNOME will notice that the original directories are missing, and it will create new ones with default settings like when you first installed Ubuntu.

If it works, your fonts should all be back to normal. Note: You'll have to redo your GNOME settings.

If it doesn't work, you can simply delete the newly created .gconf, .gnome2 and .config directories and rename the "old" dirs back to their original names (e.g. .gconf-old --> .gconf)

---

### Post by zero7404 on 2009-05-13
> **Gidskid said:**
> Oh sorry, I can't read it because I am not Greek. Also it's not actually in Greek, it's just the font.

i was referring to the real fonts and libraries that can be downloaded from synaptic, this problem stated by the thread seems to be something different....

---

### Post by Gidskid on 2009-05-13
How do i get to these directories?

---

### Post by unutbu on 2009-05-13
Gidskid, in the file browser (nautilus), press Ctrl-h to show files and directories that begin with a period. So-called dot-files are hidden by default.

Look for .gconf, .gnome2, and .config in the top level of your home directory.

---

### Post by Gidskid on 2009-05-13
You Fixed it!

Thanks a lot for helping me out!


-G

---

### Post by unutbu on 2009-05-13
Yay! \\:D/
Enjoy Ubuntu.

---

