---
title: "Can't find new installed software"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-10-22
here we go: another stupid newbie question =)

i installed 7zip so i can extract some rar files... but, for some reason, i can't get it working after the installation, nor can i see it on the main menu! why is that? =/

---

### Post by rossmoore on 2009-10-22
I find the standard archive software that comes with ubuntu is sufficient (file roller, or archive roller or something?). If you can't find it in the menu (it might be put somewhere slightly unexpected, like Accessories, or even System Administration), can you run it from the command line?

---

### Post by ad_267 on 2009-10-22
It isn't a separate application. It adds support for RAR and other files to the default file archive manager. So just treat any rar files like you would a zip file.

Also, how did you install p7zip exactly?

---

### Post by sahabcse on 2009-10-22
#apt-cache search package

eg) apt-cache search mp3

---

### Post by running_rabbit07 on 2009-10-22
I have had a few installs where I have had to log out and back in to get the program to show up in the menu.

---

### Post by rossmoore on 2009-10-22
Ah, well I guess that explains why it isn't in the menu - it's just a plugin for the existing archive software that comes bundled (Archive Manager I think it's called, with a roller icon).
I unarchive rar files, and I don't remember having to install anything to deal with them though.

---

### Post by martrn on 2009-10-22
I **think** p7zip is just the cli version for linux of the various file formats and has no GUI so even if you installed it, i do not **think** there is a version of 7zip (gui) for ubuntu.

Have you tried peazip which is a gtk/qt front end for all the compression system simular to what you would find on a windoze box.

```
sudo apt-get install peazip
```.

---

### Post by Konbuntu on 2009-10-22
i tried extracting it with archive manager but it didn't work. i downloaded 7zip from "add/remove applications"... anyways, maybe martrn is right: ubuntu doesn't support this software.
i will try peazip!


thanks everyone!

---

### Post by ad_267 on 2009-10-22
Hmm, well I usually install the rar and unrar packages rather than p7zip, but I assumed it would work the same way.

Try installing RAR from Add/Remove instead and then use the default archive manager (It's called File Roller, but is just called Archive Manager in the menu).

---

### Post by Konbuntu on 2009-10-22
tried dl peizip. this is what i get: There is no matching application available. 

i got the same thing by using the terminal with the command provided above...

---

### Post by g160689 on 2009-10-22
there could be dependency modules
installing any software from internet is a safer way

---

### Post by ad_267 on 2009-10-22
> **g160689 said:**
> there could be dependency modules
installing any software from internet is a safer way

It's always safer to install software from the Ubuntu repositories than from a website.

Just install RAR from Add/Remove and that should work fine. Or use:
```
sudo apt-get install rar unrar
```

---

### Post by Konbuntu on 2009-10-22
thank you! i dl rar :guitar:

---

### Post by martrn on 2009-10-22
You can download peazip in .deb format from :
[http://peazip.sourceforge.net/]("http://peazip.sourceforge.net/").

You might need to add a repository to find peazip if it is not in one of your repositories.

---

