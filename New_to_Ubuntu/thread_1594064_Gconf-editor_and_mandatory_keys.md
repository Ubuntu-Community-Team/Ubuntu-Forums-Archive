---
title: "Gconf-editor and mandatory keys"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-10-12
So I was having an issue where fiddling with themes would cause my buttons to set to windows default. I've grown quite attached to the mac layout over time, so I went into gconf-editor and reset them to mac setup. However, I didn't quite get the arrangement correct and I set the key as mandatory. Now, reading into it, the way to get the key to cease its unwritability is to select Unset Key, however, both before and after I do this, I get this error message when I try to set the key:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/metacity/general/button_layout' set in a read-only source at the front of your configuration path

Can someone help me fix this?

---

### Post by mcduck on 2010-10-12
When you set the key as mandatory you probably were asked for a password? That's because Mandatory values are handled by root (what would be the point if the normal user's could change them? ;))

Anyway, gconf-editor seems to automatically ask sudo password when trying to set a mandatory value, but gives no similar way for unsetting one. Instead you'll have to run "gksudo gconf-editor", then select File/New Mandatory Window". You'll get a list of all the mandatory keys on your system, and will also be able to unset the keys there.

---

### Post by Zeppelin! on 2010-10-12
Um, thank you, but that only makes a difference for root. I can unset the key, set it as default, rearrange it, whatever, but those changes only apply to root. I have to go back to regular gconf-editor where the key is different and it still won't let me write it.

---

### Post by mcduck on 2010-10-12
Mandatory & default keys should be configurable by root only, and affect all users. At least that's how it has always worked before, and should still work according to Gnome's documentation.

[http://library.gnome.org/users/gconf-editor/stable/defaults-mandatory.html.en]("http://library.gnome.org/users/gconf-editor/stable/defaults-mandatory.html.en")

---

### Post by Zeppelin! on 2010-10-12
Well, I play with the settings in gksudo gconf-editor all I like but it is having no effect on the actual settings. no matter how many times I set close,minimize,maximize: it just stays menu:minimize,maximize,close
Even better, root thinks the setting *is* close,minimize,maximize: Even though it quite clearly isn't.

I'm thinking we have a problem, really. My settings match neither those seen with gksudo gconf-editor nor gconf-editor. Further, despite having on multiple occasions demandatoried the key (having set it as mandatory for the express purpose), and set it as default, and edited it, in the regular version it remains uneditable.

Is there some way to get at these settings outside of gconf?

---

