---
title: "Delete Trash contents"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by donescamillo on 2010-09-07
Hi,

I had two user accounts on my system. One of them might have had files in Trash can when I deleted that user account. From the other account I can see there are files in the Trash can. I assume they might be leftovers from the other user account (the deleted one). I cannot delete them. Nautilus says "Failed to delete the item from Trash". How can I delete the files from Trash?

Thanks

---

### Post by muteXe on 2010-09-07
open up nautilus as root i guess.

gksudo nautilus

be careful though :)

---

### Post by Meltedfusion on 2010-09-25
> **muteXe said:**
> open up nautilus as root i guess.

gksudo nautilus

be careful though :)

Good Morning. I am having the same problem...I actually entered gksudo nautilus but when I right click on trash empty trash is greyed out. when i try to open in new window or just click on trash to enter the folder i get 
The folder contents could notbe displayed.
Sorry, could not display all the contents of "trash": Operation not supported. 
Any help would be much appreciated. Im using 10.04 that was upgraded from 9.10.
If you need me to post any outputs please let me know.
Thanks in advance.

---

### Post by sudeepk on 2010-09-25
Try from terminal.

First view the files in the trash.

ls $HOME/.local/share/Trash/files

If you can see anyone of them the delete them using the following command.

rm -rf $HOME/.local/share/Trash/files/*

$HOME is your user home. 

Becarefull. If you are logged in as a root then your home will be /root

---

