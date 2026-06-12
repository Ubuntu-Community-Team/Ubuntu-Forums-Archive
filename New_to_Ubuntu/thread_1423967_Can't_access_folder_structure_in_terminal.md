---
title: "Can't access folder structure in terminal"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by pylorns on 2010-03-07
I have mounted additional hard drives called Terra_1 and under that I have a folder called HD Movies  with a space.  every file in there has a pad lock on it - I copied from my windows machine to this shared folder and on my ubuntu machine it says I'm not the owner of these copied files.  When I go to terminal I go to my media/Terra_1 mount and then try to access the folder HD Movies - and I can't.  Says folder not found.  With the space it says can't find "HD"  if I put an underline it says can't find the whole string.  The gui shows it with a space.

Thoughts?

---

### Post by patchwork on 2010-03-07
cd HD\ Movies

or cd "HD Movies"

The terminal doesn't read through whitespace in filenames or directories without explicit directions.

---

### Post by pylorns on 2010-03-07
That worked. Thanks!

---

### Post by MooPi on 2010-03-07
Rename the folder without space. Open a terminal and ```
sudo chown -R username /media/Tera_1/HDMovies
``` You are now the owner of siad files and should be able to read and play the video.

---

### Post by pylorns on 2010-03-07
How can I take ownership of all the files in that folder?

---

### Post by pylorns on 2010-03-07
Again - also worked - both questions answered and fixed my problem thanks!

---

### Post by beegary on 2010-03-07
Are you aware you can use 'Autocomplete' in terminal using the TAB key

---

### Post by pylorns on 2010-03-07
No but I see how it works now.

---

