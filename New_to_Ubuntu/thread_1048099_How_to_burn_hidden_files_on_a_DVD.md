---
title: "How to burn hidden files on a DVD"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by andy08 on 2009-01-23
Hi,

I'm reelly new to Linux. I've been testing it for about 2 weeks now.And I love to use it. All worked fine until I decided to use Ubuntu as my primary OS. I need to reinstall and change all partitions.
I want to backup Mozilla Firefox and Thunderbird on a DVD. But these files are hidden files and I can't burn them. I don't want that my bookmarks and emails get lost. 
Could someone help?
Thanks very much  in advance:(

---

### Post by brsmits on 2009-01-23
you could just copy the contents of the hidden files (probably something like ~/.firefox) into a non hidden folder, then burn that one.

---

### Post by mcduck on 2009-01-23
The best way is to compress all the stuff you want to backup into a .tar.gz archieve (like a .zip file). It is possible to backup the dotfiles without doing this, but putting everything into a .tar.gz has the benefit that it will store file permissions as well.

To do it in a GUI, open the file manager, go to your home directory, press Ctrl-h to dispaly hidden files. THen select everything you want to include in the backup, right-click and select "Create Archive" from the popup menu. Set the archive format to .tar.gz or .tar.bz2 and click "Create". 

Now you can easily burn the created archive file to CD/DVD. :)

---

### Post by iaculallad on 2009-01-23
Simple. While logged on your account, click on Places->Home Folder to open your user folder using nautilus. Once opened, press Ctrl+H to show all hidden files and folders. Copy the hidden folder you want to backup to a new *unhidden* folder for burning.

---

