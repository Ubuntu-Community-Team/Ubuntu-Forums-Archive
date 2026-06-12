---
title: "update manager error"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by manuleka on 2009-01-22
everytime i run update i get this error message... how can i fix it?
```

W: Failed to fetch http://wine.budgetdedicated.org/apt/dists/intrepid/Release.gpg  Could not resolve 'wine.budgetdedicated.org'

W: Failed to fetch http://wine.budgetdedicated.org/apt/dists/intrepid/main/i18n/Translation-en_NZ.bz2  Could not resolve 'wine.budgetdedicated.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Nevyn on 2009-01-22
In System -> Administration -> Software Sources; do you have the multiverse and restricted boxes checked?

---

### Post by thomasyen on 2009-01-22
Did you add the GPG key for the Wine repository? Because your entries appear to be referring to the GPG key not being added.

---

### Post by sh4d0w808 on 2009-01-22
Possibly the mentioned resources not available, or your network connection have broken or misconfigured.

---

### Post by manuleka on 2009-01-22
multiverse and restricted ticked...

I don't understand what you mean Thomasyen about GPG Key

this error came up when i added wine (added a line to the software sources) but the wine installation went through and i'm using it now... for running ies4linux...

i just don't know why it always brings up the error...

---

### Post by jgoguen on 2009-01-23
To import the GPG key, download [Scott Ritchie's GPG key]("http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg") and save it somewhere, like in your home directory.  Then open Software Sources (System -> Administration -> Software Sources) and choose the **Authentication** tab.  Click the **Import Key File...** button, choose the file you saved (it's named **Scott Ritchie.gpg**) and it will import the required GPG key.

That, however, is not why you're getting those errors. You appear to have **wine.budgetdedicated.org**, when you should have **wine.budgetdedicated.com**.  In the Software Sources window, go to the **Third-Party Software[b] tab, click the entry that says [b][http://wine.budgetdedicated.org/apt](http://wine.budgetdedicated.org/apt) intrepid main**, click the **Edit** button, and a new window will come up.  In the **URI** box, change **org** to **com**.  The **URI** box should contain this text when you're done (you can also just copy/paste this text if you want):
```
http://wine.budgetdedicated.com/apt
```
I believe that may be my fault from another thread, where I made the same mistake in telling you what line to look for, but not in telling you what line to add.  Sorry for the confusion :(

---

### Post by manuleka on 2009-01-27
thanks jgoguen :) that fixed it...

---

