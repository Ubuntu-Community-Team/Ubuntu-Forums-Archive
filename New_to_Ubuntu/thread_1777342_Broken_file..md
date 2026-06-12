---
title: "Broken file."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Visharana on 2011-06-07
I've recently updated to 11.04 and the hidden file that I had before is now 'broken'.  Is there a way to access or unbreak it?

---

### Post by nothingspecial on 2011-06-07
> **Visharana said:**
> I've recently updated to 11.04 and the hidden file that I had before is now 'broken'.  Is there a way to access or unbreak it?

Do you mean link?

You need to post more info.

---

### Post by Rex Bouwense on 2011-06-07
Is this a program file?  There is a procedure for fixing broken packages in the Synaptic Package Manager under custom filters.  Is that what you are looking for?

---

### Post by dFlyer on 2011-06-07
> **Visharana said:**
> I've recently updated to 11.04 and the hidden file that I had before is now 'broken'.  Is there a way to access or unbreak it?

What hidden file? How is it broken? Is it a package? Have you tired:

sudo apt-get -f install

---

### Post by AlphaLexman on 2011-06-07
From a terminal, post the output of:
```
file /path/to/file/.filename
```
Note the dot in front of the filename, that means it is hidden.

---

### Post by Visharana on 2011-06-07
Sorry... before the upgrade, my Pictures file was a hidden file because of making icons/graphics for web pages and such that I didn't want the kiddos into... 

After the upgrade, this file is no longer hidden, but it says it cannot be opened because it's broken.  There are (or were) thousands of pictures in this file.

I've done the file search method, and it still can not be opened because it is broken.

---

### Post by nothingspecial on 2011-06-07
Was it a symbolic link?

I can't think of another reason the "file" would be broken (but then my kids are running around screaming so I may be missing something obvious).

---

