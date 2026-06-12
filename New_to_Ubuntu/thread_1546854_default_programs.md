---
title: "default programs"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Jedcurtis on 2010-08-06
So where are the applications I use, (like transmission for example) when I want to assign them the status of being the default app to open stuff with?  Like, where does Ubuntu install all of its app files to?  Can I add programs to the default prog list?  By the way, I blew away my Windows7 Ultimate OS so I could have a stand alone laptop with Ubuntu 10.04 on it.  Works AWESOME! Go Ubuntu!!!

---

### Post by jtarin on 2010-08-06
> **Jedcurtis said:**
> So where are the applications I use, (like transmission for example) when I want to assign them the status of being the default app to open stuff with?  Like, where does Ubuntu install all of its app files to?  Can I add programs to the default prog list?  By the way, I blew away my Windows7 Ultimate OS so I could have a stand alone laptop with Ubuntu 10.04 on it.  Works AWESOME! Go Ubuntu!!!To fine the directories where Ubuntu looks first for the executables...enter the command ```
PATH
```in your terminal.

The easiest way to use Transmission as a system-wide default is to download a .torrent file (save it to your disk), navigate to the .torrent file in Nautilus file manager, and right click the file.
Then select "Properties", then the tab "Open With", then choose the program you would like to always open your .torrent files. You may need to log out and back in to see the changes, but probably not. This can be applied to any file you have that you want to assign a default.

To locate files first enter the command ```
sudo updatedb
```it will run for awhile, the first time updating the database of your install. When finished running you can use the command ```
locate <filename>
```to find any instances of that name in your install. If it returns nothing....then in all probability it is not installed. There are other methods of finding files but this will suffice in most cases.

---

### Post by Jedcurtis on 2010-08-06
Thanks for the quick response.  One of the wonderful things about Ubuntu, is the willingness of the community to help one another.  You solved my problems, and answered all my questions.  Couldn't ask for more...:)
Jed

---

### Post by jtarin on 2010-08-06
Your more than welcome. I wish most users were as appreciative by responding.

---

