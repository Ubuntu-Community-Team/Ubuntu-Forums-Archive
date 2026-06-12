---
title: "Making xrandr change permenant"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Bodhibear420 on 2009-12-26
Hello,
I managed to add the custom resolution I was looking for through xrandr.  Now when I try to set up those lines to etc/gdm/presession/defaults it tells me it is a read only file.  So, I need to find a way to either write the xrandr changes into this file or else figure out another way to make that resolution option permenant.  Any help would be appreciated.  Thank you

---

### Post by spiderbatdad on 2009-12-26
believe you can write file /etc/gdm/Init/:0
make it executable.
#!/bin/sh
xrandr --option and so on

or make your defaults file executable
```
sudo chmod +x /etc/gdm/file_to_make_executable 
```

---

### Post by Bodhibear420 on 2009-12-26
When I try to run that line in the terminal it just says "No such file or directory"  If it makes any difference, I am running Karmic.  The init/defaults is a read only file as well.

---

### Post by spiderbatdad on 2009-12-26
which command returns error? If you already have the file you wrote, you can make it executable. If you're trying the file I suggested, you have to write the file with nano or gksu gedit. Why don't you first try making the file you edited executable. With the command I added to above post.

---

### Post by spiderbatdad on 2009-12-26
ok sorry Bodhibear420, I think I see the problem. You have to edit the file with a text editor. Additionally you'll need to be superuser. So try the command ```
sudo nano /etc/gdm/presession/Default
``` Use ctrl+o and enter to save, then ctrl+x to exit.

---

### Post by Bodhibear420 on 2009-12-26
alright, so I've opened that up, entered this:

  	 	 	 	 	 	  xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
 xrandr --addmode VGA1 1280x800_60.00
xrandr --output VGA1 --mode 1280x800_60.00

and then ctrl+o, enter
before I can exit, it states at the bottom

 [ Error writing /etc/gdm/presession/Default: No such file or directory ]

any thoughts?

---

### Post by spiderbatdad on 2009-12-26
yes. looks like I had a bad file name in the command The directory is Presession with capitol P. You must enter file names in case sensitive manner. It help to cd into Directories and ls to see the files. For example:
```
cd /etc
ls
cd gdm
ls
cd Presession
ls
```and so on. To go back one level
```
cd ..

```
To return to home
```
 cd 
```
Hope this helps.

---

### Post by Sir Jasper on 2009-12-26
Hi,

For an alternative and simple method that is likely to work - see:

[http://ubuntuforums.org/showthread.php?t=1332296&highlight=1024&page=4](http://ubuntuforums.org/showthread.php?t=1332296&highlight=1024&page=4)

#15 on page 2 and #33 on page 4.

My regards

---

### Post by Bodhibear420 on 2009-12-26
Fantastic Spiderbatdad, that worked out perfectly.  Thank you for all of the help.  Thanks for the second option Sir Jasper, I'm happy I didn't even have to try it.  Thanks all

---

