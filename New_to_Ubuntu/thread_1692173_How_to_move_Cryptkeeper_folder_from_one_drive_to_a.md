---
title: "How to move Cryptkeeper folder from one drive to another?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by foogoo on 2011-02-21
Hi, I think this is a pretty basic question but surprisingly couldn't find the answer in any searches.

My notebook died earlier this week but all the data is intact, including an encrypted Cryptkeeper folder. When I get my new computer set up, how do I move that folder over? In other words, where does Cryptkeeper store the encrypted folders?

Thanks.

---

### Post by fabricator4 on 2011-02-21
> **foogoo said:**
> When I get my new computer set up, how do I move that folder over? In other words, where does Cryptkeeper store the encrypted folders?

Cryptkeeper puts the folder exactly where you tell it to, but makes it a hidden folder.  That is, it puts a '.' in front of the filename and it will not show up in a normal directory listing.  Under Nautilus click view and "show hidden files" or in terminal display all files:
ls -a

Be warned though, you can't just copy the contents of the directory into another unencrypted directory - Cryptkeeper will not recognise it and you'll just have some encrypted files in an unencrypted directory, even you manage to get the hidden .xml file that is there.

I found it was possible to move the encrypted directory in it's entirety and then import it into Cryptkeeper.  To import the directory open Cryptkeeper/Import Ncfs Folder then right click on the file selection window, then select "show hidden files" from the menu.

Chris

---

