---
title: "uninstall a bin file"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by vagelism on 2009-09-12
Hello to all . As a new user I installed google earth from a bin file. Now I want to uninstall it and I do not know how.
I do not think I have the bin file anymore.
Can any one help me please.
Thank you.

---

### Post by jflaker on 2009-09-12
> **vagelism said:**
> Hello to all . As a new user I installed google earth from a bin file. Now I want to uninstall it and I do not know how.
I do not think I have the bin file anymore.
Can any one help me please.
Thank you.

Think of a bin (binary) file as a .exe file.  Right click on it, then properties, then to the permissions tab....
Make sure "Allow executing file as program" is checked and it will run.

Remember, there are no real file types, like in windows, that are programs...they all can be programs.

That being the case, just delete the bin file and it is gone.

Good luck.

---

### Post by vagelism on 2009-09-12
yes but now ...how can i uninstall the googleearth....that i installed by bin file...
thank you

---

### Post by nickmcg on 2009-09-12
There's no really easy way to do this - googleearth doesn't have an uninstall utility that I've found.

But:

in terminal ```
sudo find / -iname 'google*'
``` will list most of what you need to delete. If you're not confident using 'rm' then launch nautilus from the terminal ```
sudo nautilus
``` and delete the googleearth files.

you will also find in your home directory a folder '.googleearth' which you may also want to delete.

HTH

Nick

---

### Post by NoaHall on 2009-09-12
After finding and deleting, run "sudo ldconfig"

---

### Post by nickmcg on 2009-09-12
Thanks for that - I'd wondered how to tidy that up

Nick

---

