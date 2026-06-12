---
title: "Error moving file: Permission denied?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-10-20
I'm trying to install a new skin for amsn, so i'm following this tutorial: 

The plugin should appear in the plugins selector dialog. You don't need to restart aMSN. 
To install a skin just download it, and extract the files for the .zip file (.zip, .tar.gz, or similar). Then copy the extracted skin folder to one of the following locations: 
  /usr/share/amsn/skins
 $HOME/.amsn/skins

for some reason, when i drag the folder containing the new sking, ubuntu says
have no permission: "Error moving file: Permission denied"

=/

---

### Post by anewguy on 2009-10-20
Check the permissions of the folder you are copying into - for instance, check the permissions of /usr/share/amsn/skins - you may find that only the owner has permissions to write there (like /usr itself does) and you aren't the owner (for /usr, the owner is root).

Try the following in a terminal window:

gksudo nautilus

just enter in your normal password when prompted.  This should start the GUI'd file browser as if you were root.  You will need to first navigate to where the folder/files are that you want to copy or move, then either highlight them and copy/paste or drag them to the folder you want.

Dave :)

---

### Post by swoody on 2009-10-20
The /usr directory is owned by the root user. To move files to there, you will can use a command from the terminal. Open a terminal (Applications>Accessories>Terminal) and enter:
```
sudo mv /path/from/file /usr/share/amsn/skins/
```

The /.amsn/skins directory is in your home folder, and you are able to drag/drop files to it. Just open your /home folder with Nautilus, and press 'Ctrl+H' to view the hidden files. You should find '.amsn' there. If not, you can create the folder named ".amsn" and the "skins" folder within that.

Hope this helps you out a bit  :)

---

### Post by Konbuntu on 2009-10-20
anewguy
swoody

thanks =)

---

### Post by swoody on 2009-10-20
No problem at all, glad it worked for you :D

Just FYI, it may be useful if you could mark your thread as [SOLVED] when your question(s) have been answered. Simply click on 'Thread Tools' in the top-right of this page, and select 'Mark thread as solved'. Thanks :)

---

### Post by anewguy on 2009-10-20
You're welcome.

Dave :)

---

