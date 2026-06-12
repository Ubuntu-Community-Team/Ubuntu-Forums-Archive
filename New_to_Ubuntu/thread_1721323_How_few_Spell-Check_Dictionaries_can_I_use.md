---
title: "How few Spell-Check Dictionaries can I use?"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-04-04
For spell-checking, I need to be able to use English & French dictionaries.

I need this facility in (at least) OpenOffice, Thunderbird & Gedit.

Does that mean installing English & French dictionaries in each application, or can at least some of them share dictionaries?
Depending maybe on where the dictionaries go??

I searched without finding any general guide to dictionaries in Ubuntu...

Thanks for any helpful suggestions!

---

### Post by shafin on 2011-04-04
Unfortunately openoffice and thunderbird are not gtk applications, so it is hard to get shared dictionaries to work.
For thunderbird, go to Edit>Preferences>Composition>Spelling. Chance is the english dictionary is already installed. There is a link to download more dictionaries, you can install the french one from there.
In openoffice go to Tools>Options>Language Settings. there you can find the dictionaries used and have links to install more.
For normal gnome applications like Gedit, you need to install aspell-en and aspell-fr packages.

---

