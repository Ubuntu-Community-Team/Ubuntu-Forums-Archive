---
title: "backintime will not open in gnome"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-01-07
when i use the menu i see it open for a second then it closes. when i use  the command line i get

lance@bermudezl:~$ backintime-gnome
Back In Time
Version: 0.9.26

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime-gnome --license' for details.

/usr/share/backintime/gnome/app.py:1051: Warning: g_set_prgname() called multiple times
  gnome.program_init( 'backintime', cfg.VERSION, properties = gnome_props )
Traceback (most recent call last):
  File "/usr/share/backintime/gnome/app.py", line 1056, in <module>
    main_window = MainWindow( cfg, app_instance )
  File "/usr/share/backintime/gnome/app.py", line 281, in __init__
    self.update_all( True )
  File "/usr/share/backintime/gnome/app.py", line 388, in update_all
    self.update_folder_view( 1, selected_file, show_snapshots )
  File "/usr/share/backintime/gnome/app.py", line 1000, in update_folder_view
    new_iter = self.store_folder_view.append( [ item[0], rel_path, item[3], item[5], item[1], item[2], item[4] ] )
TypeError: value is of wrong type for this column
lance@bermudezl:~$ 

how do i fix this? I completly uninstalled it and reinstalled the program

---

### Post by lance bermudez on 2010-01-07
for some reason the program will work if i do the gnome root option for backintime

---

### Post by R4isen on 2010-01-13
Simply delete config file of backintime "/home/r4isen/.config/backintime/config" or, if you want you can try to edit this file.

Yeah i know that's old topic but 10 min ago i've had the same problem and i couldn't find solution.

---

### Post by DThurman on 2010-06-29
Back In Time's Applications->System Tools still
shows the icons even though it is not installed...

I tried to edit the menu and untick the icons but
they do not appear there.  I looked into my $HOME/.config,
not there either.

The backintime package does not appear to remove the
icons when purging or removing the package, I tried
it.

So, how do I get rid of it?

---

### Post by m.maga on 2010-10-14
Hi R4aisen,

I realized that the last_path was causing the problem in .config/backintime/config. So I changed it:

FROM:
gnome.last_path=/home/share/VirtualBox/HardDisks

TO:
gnome.last_path=/

I dunno why the problem occurs, but the path "/home/share/VirtualBox/HardDisks" seems to be ok in the file system. If I leave Backintime in that path, the problem is back.

---

### Post by m.maga on 2010-10-14
The main reason for this backintime bug is here: [https://bugs.launchpad.net/backintime/+bug/409130/comments/9](https://bugs.launchpad.net/backintime/+bug/409130/comments/9).

---

