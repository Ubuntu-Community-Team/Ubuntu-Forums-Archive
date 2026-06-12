---
title: "uninstalling wine run windows programs"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by megaultranoob on 2009-09-16
I have been trying with no success to get rid of a malfunctioning Google sketchup I tried to run in wine. I run the uninstaller over and over and lo, there it is, same condition as before, icons mocking me, shredded pieces beshitting my hard drive. 
How do I get rid of it fully? Clearly, parts are not being removed or the uninstaller isn't working properly. Do I do it manually? How?
Thanks

---

### Post by LowSky on 2009-09-16
go to your /home folder, hit CTRL+H to un hide some folders, fine the one named .wine, inside it will be a c folder, in there you will find program files, delete the folder named after the program and say goodbye. 

For the Applications menu
right click on applications, choose menu, find the progrma o the list under wine and delete.

---

### Post by HarrisonNapper on 2009-09-16
If you have the issue when reinstalling wine after a full uninstall, let us know and we can check your wine configuration and emulated C drive.

---

### Post by por100pre1 on 2009-09-16
Maybe the program is gone but the launcher is hidden in ~/.local/share/applications/wine/Programs . Open your user folder and press CTRL+H to find the hidden .local folder. You can also clean the .wine folder.

---

### Post by megaultranoob on 2009-09-16
That got it. Thanks to all! Ubuntunate!

---

