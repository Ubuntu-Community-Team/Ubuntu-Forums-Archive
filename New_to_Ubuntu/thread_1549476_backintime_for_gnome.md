---
title: "backintime for gnome"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-08-09
I was told that 

Simply delete config file of backintime "/home/r4isen/.config/backintime/config" or, if you want you can try to edit this file

would fix my problem about it not working as in saying open when you click on it.

File "/usr/share/backintime/gnome/app.py", line 1056, in <module>
    main_window = MainWindow( cfg, app_instance )
  File "/usr/share/backintime/gnome/app.py", line 281, in __init__
    self.update_all( True )
  File "/usr/share/backintime/gnome/app.py", line 388, in update_all
    self.update_folder_view( 1, selected_file, show_snapshots )
  File "/usr/share/backintime/gnome/app.py", line 1000, in update_folder_view
    new_iter = self.store_folder_view.append( [ item[0], rel_path, item[3], item[5], item[1], item[2], item[4] ] )
TypeError: value is of wrong type for this column

it is not fixing it so what am i doing wrong?

---

### Post by jtarin on 2010-08-09
Could you state your problem in greater detail? Have you used the application successfully before?

---

### Post by lance bermudez on 2010-08-10
the way i fixed the problem in the past is not working. after i configure the program using backintime-gnome and click ok the program opens and closes at the same time so i tried it from the command line to open it and the above is the error message for backintime-gnome from the command line.

---

### Post by jtarin on 2010-08-10
Try removing completely and then reinstall.Delete those config files before.

---

### Post by lance bermudez on 2010-08-11
did that to and it will still not work like it is supposed to

---

### Post by jtarin on 2010-08-11
Did it _**ever**_ work correctly?

---

### Post by jhoyne on 2011-03-09
I have come across this problem and found a solution in bug reports. Apparently this error occurs if a file in your backup exceeds 3GB in size. The solution (at least worked for me) is:

Edit backintime's app.py file

```
gksu gedit /usr/share/backintime/gnome/app.py
```
Change line 212 from:

```
self.store_folder_view = gtk.ListStore( str, str, str, int, str, str, int )

```
to

```
self.store_folder_view = gtk.ListStore( str, str, str, int, str, str, float )
```

more info [https://bugs.launchpad.net/backintime/+bug/409130]("https://bugs.launchpad.net/backintime/+bug/409130")

---

