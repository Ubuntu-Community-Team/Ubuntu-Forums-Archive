---
title: "Removing Trash and Junk Folders in Evolution"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Joseph Schwenker on 2009-08-15
I use Gmail with IMAP and Evolution 2.26.1 on Ubuntu 9.04.  Evolution displays two folders under my Gmail account: "Trash" and "Junk".  I already have trash and spam folders inside Gmail, and I already delete messages by dragging them to Gmail/Trash.  Is there any way that I can remove the junk and trash folders under my Gmail account from Evolution?  The delete option is grayed out, and Folder/Delete does nothing.  Thanks in advance!

---

### Post by giancarlo76 on 2009-09-08
I've got the same problem, or at least I see it as a big problem...

In Thunderbird this is as simple as adding an option to pref.js:
```
user_pref("mail.server.server2.trash_folder_name", "[Gmail]/Trash");
``` Then I can use the Trash folder without any problem.

I can say this apparent lack of feature leaves me away from using Evolution, because I can't find any exaustive documentation on how to setup it following my needs. I don't want Evolution to put the mail I mark as 'deleted' in a virtual folder on THIS computer, because I want to access the deleted mail from, say, Thunderbird on another PC.
So, please, if it is possible to let Evolution put the deleted messages in a folder I specify, tell us how can this be achieved!
I guess a possible solution is overriding the server's namespace, but again, the lack of exhaustive documentation on how to do it (what do I have to write in the 'namespace' field?) prevents me to use this feature.
In the meanwhile, I'll go back to Thunderbird.

---

