---
title: "Thunderbird folder columns"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Michael Dooley on 2009-12-13
I recently installed Thunderbird 3 on my 8.04 ubuntu OS replacing Thunderbird 2. However, I could find no way for Thunderbird to display the total amounts of files in each folder. I tried installing an add-on, Extra Folder Columns, but got a message that said it was not compatible with Thunderbird 3. Is there any way I can get this extension to install? I would prefer not to go back to Thunderbird 2 if possible.

Thanks in advance for your suggestions.

---

### Post by Michael Dooley on 2009-12-14
This worked for me.

I had to edit the install.rdf file that was within the extra_folder_columns-0.3-tb,xpi installation file to set maxVersion to 3.0 from whatever pre-release version was there in the first place.

I was then able to install the columns feature without the error message appearing and thunderbird showed column possiblities for my folders when restarted.

---

