---
title: "Mozilla Thunderbird Preferences: Not Launching"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by KlytusLord on 2010-03-22
Hello all,

I am using Ubuntu 9.10 64-bit and Thunderbird 2.0.0.24

In Thunderbird and in the Thunderbird address book selecting "preferences" from the edit menu fails to open any type of window showing the options available.  Nothing happens at all when I select this menu option, not even the busy cursor appears.

Everything else is working fine within Thunderbird.

All I need to do is change the setting to prevent addresses added to my address book just because I replied to them.  I want my address book to have only the contacts I have added manually.

Does anyone know how to get the preferences working or just hot to change the setting I described?

Many thanks for your help, and sorry if this is in the wrong forum.  I was not sure where to post my question.

---

### Post by r-senior on 2010-03-22
Aye, that's in Edit -> Preferences -> Composition -> Addressing.

Works for me on 9.10 with 2.0.0.24. You could try closing Thunderbird and using:

$ thunderbird -safe-mode

May not help but worked for someone having a problem with Firefox recently.

---

### Post by KlytusLord on 2010-03-22
Thank you, r-senior!

That worked.

---

