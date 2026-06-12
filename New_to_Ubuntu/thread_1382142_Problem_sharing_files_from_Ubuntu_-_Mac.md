---
title: "Problem sharing files from Ubuntu - Mac"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by daviesjohn on 2010-01-15
Hello,

I have recently started out with Linux, booting an eepc into Ubuntu 9.10.

I have attached it to my wireless network and it has internet access, and can be seen by the other machines on the network (all Macs).

I have a bunch of folders on the Ubuntu box I want to be able to copy over to another machine. I have gone into Sharing Options for each of the folders, checked share this folder, allocated a name and allowed guest access.

I can then log in to the eepc from a Mac on the same network (it shows up in the Mac Finder). 

Starting the copy is OK, and it runs fine for a few files, but then falls over. The error is:

> The Finder can&#8217;t complete the operation because some data in &#8220;&#8221; can&#8217;t be read or written.
(Error code -36)Any thoughts on what I should try changing?

Thanks,

John

---

### Post by Penguin Guy on 2010-01-15
Your Mac is being denied permission to read the files. Go to the folder properties' "Permissions" tab. Set everything to your satisfaction, and once finished click the "Apply Permissions to Enclosed Files" button. You may see half your settings disappear - don't worry, that's normal. Once you've done all that, try the download again, and tell us how it went.

P.S. I've attached a screenshot of the file permissions screen so you know what you're looking for.

---

### Post by daviesjohn on 2010-01-15
Thanks Penguin Guy for that - I have made the changes you suggested.

I still get the same problem.

Do I need to go down the whole tree and make the same changes? Some of the files are in nested subfolders on the Ubuntu machine.

Thanks, John

---

