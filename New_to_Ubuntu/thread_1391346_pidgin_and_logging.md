---
title: "pidgin and logging"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by misswham on 2010-01-26
This just started a few mins ago.  When I type the letter u in the window i get this error message

Logging stopped. Future messages in this conversation will not be logged.

what could this be and how can i stop it?  i can type any other letter except the u.

---

### Post by misswham on 2010-01-26
Also, in the drop down menu, under the options tab, where it says enable logging. that has always been checked but NOW there is a U next to it.  so i unchecked the box in front and still when i type the letter u, i get that same error message in the inst mess window.  i have NEVER noticed that U until i just logged on a few mins ago.

---

### Post by misswham on 2010-01-26
i just went to synaptic and uninstalled pidgin and reinstalled it and the same thing is occurring.  Can someone please help?

---

### Post by howefield on 2010-01-26
Reinstalling won't help unless you delete the configuration files in your home folder.

---

### Post by misswham on 2010-01-26
does it sound like thats what i need to do and how do i do it?

---

### Post by howefield on 2010-01-26
Open Places > Home and press the ctrl + H keys together. This will reveal your hidden files/folders.

Look for the pidgin (it might be called .purple) folder and rename, move or delete it.

Then when you reinstall/open Pidgin again, it will rebuild the files from scratch, you'll need to set up your accounts., but hopefully the issue will be cleared.

---

### Post by misswham on 2010-01-26
i dont see a folder named pidgin,  what else could it be called?  would it be called purple?

---

### Post by howefield on 2010-01-26
Yes, could well be purple.

---

### Post by misswham on 2010-01-26
thanks and it worked.  but now i have lost all of my past conversations.  i moved the folder to a harddrive.  is there a way to access them when needed?

---

### Post by howefield on 2010-01-26
In your old .purple folder that you moved, they should be in /logs.

Copy/paste the files into your new .purple/logs folder.

---

