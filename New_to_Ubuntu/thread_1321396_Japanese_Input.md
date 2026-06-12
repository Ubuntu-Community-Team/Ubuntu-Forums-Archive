---
title: "Japanese Input"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by dsanjo on 2009-11-10
I downloaded and installed Ubuntu 9.10. It looks great and runs very fast. The problem is I cannot get Japanese input. I have a Japanese keyboard, but I want my OS, menus (and etc.) to be displayed in English. **How can I toggle between alphabet and Japanese input like in Windows?** I checked the forums but the info available for the problem is for Ubuntu 8.10, and it doesn't seem to apply to 9.10. Please forgive me, I am new to Linux.

---

### Post by coldReactive on 2009-11-10
This bug may be of use:

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/464060](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/464060)

---

### Post by -j0nn13b01- on 2009-11-10
Um, have you installed Anthy? It uninstalled for me when I installed Karmic. Look for scim-anthy in synaptic.

---

### Post by Anuovis on 2009-11-10
These steps helped me, not sure if it is the best solution.

1. System>Administration>Language Support
Add Japanese, check all the components (fonts, spell check, etc.)

2. System>Preferences>IBus preferences
Two things here. Set the on/off shortcut in the first panel, this will toggle the language bar. Ctrl+Space is convenient for me.
Then go to Input Method tab and add Japanese Anthy with a big gold crown. Other inputs are weird, so I stick to this one.

3. Open some text document. Press ctrl+space or whatever shortcut you defined in step 2. The Language bar will appear. You can click the white i button on it (next to the star) and customize all the shortcuts for swapping kana-romaji inputs. Just make sure you don't use same the same key combinations as in step 2.

I think this should work if you don't have any bugs.

---

### Post by coldReactive on 2009-11-10
> **Anuovis said:**
> These steps helped me, not sure if it is the best solution.

1. System>Administration>Language Support
Add Japanese, check all the components (fonts, spell check, etc.)

2. System>Preferences>IBus preferences
Two things here. Set the on/off shortcut in the first panel, this will toggle the language bar. Ctrl+Space is convenient for me.
Then go to Input Method tab and add Japanese Anthy with a big gold crown. Other inputs are weird, so I stick to this one.

3. Open some text document. Press ctrl+space or whatever shortcut you defined in step 2. The Language bar will appear. You can click the white i button on it (next to the star) and customize all the shortcuts for swapping kana-romaji inputs. Just make sure you don't use same the same key combinations as in step 2.

I think this should work if you don't have any bugs.

Japanese can't do spell check from the language support dialog. Installing these things might remove the ubuntu-desktop metapackage, don't worry though.

---

### Post by Anuovis on 2009-11-10
> **coldReactive said:**
> Japanese can't do spell check from the language support dialog. Installing these things might remove the ubuntu-desktop metapackage, don't worry though.

My mistake, the spell check is not really there. I just wanted to say it is better to check all components available but yes, not of them are in the first place.

Did I remove the desktop metapackage as well? What do you mean by *installing these*?

---

### Post by coldReactive on 2009-11-10
> **Anuovis said:**
> My mistake, the spell check is not really there. I just wanted to say it is better to check all components available but yes, not of them are in the first place.

Did I remove the desktop metapackage as well? What do you mean by *installing these*?

Installing The Japanese/Thai/Chinese language files will remove ubuntu-desktop metapackage for some strange reason and install stuff like anthy and ibus-anthy/etc.

---

### Post by Anuovis on 2009-11-10
> **coldReactive said:**
> Installing The Japanese/Thai/Chinese language files will remove ubuntu-desktop metapackage for some strange reason and install stuff like anthy and ibus-anthy/etc.

What is that metapackage for?
Well, IBus and some weird Anthy was on my system by default. The only noticable change after language installation was that another Anthy input appeared, the only one actually usable.

---

### Post by dsanjo on 2009-11-10
Thank you everyone! The advice from Anuovis worked. I am now translating documents at work, thanks to you. &#12393;&#12358;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;

---

### Post by Anuovis on 2009-11-10
&#12364;&#12435;&#12400;&#12387;&#12390;&#12367;&#12384;&#12373;&#12356;:)
You might want to mark this thread as solved.

---

### Post by Palomar70 on 2009-12-29
I have exactly the same problem of dsanjo, who started the thread.
I followed the instructions by Anuovis, but it still doesn't work.
Anthy doesn't appear on the bar.
How could I do?
Thanks
Marco

---

