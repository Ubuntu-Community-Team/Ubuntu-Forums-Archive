---
title: "cursor trouble i have tried both ways"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by mechanicforme on 2008-12-10
Hello there ok i have just updated to ubuntu 8.10 and i dowloaded a cursor from gnome-look i first tried gcursor but its like te buttons dont work inside the program so it was useless and then i tried extracting the cursor file into home/usr/icons but it tells me the the extraction was denied that i dont have the authority to do so so i tryed moving it into filesystem/ect/x11/cursors, but i get the same problem and i went to user to check authority and thats not it so i am sitting here stumped  :confused: any help would be great thanx S.B

---

### Post by Hospadar on 2008-12-10
all those files (in /usr and /etc) are owned by the root (administrator) user.  The reason is to protect you from accidentally deleting/changing stuff in them.

Anywho, you need to give yourself root privileges to be able to put files in these locations.  If you're familiar with the terminal at all you can use "sudo" but probably the easiest way would be to open a nautilus (the file browser) window as root and do whatever you need from there.

if you do Alt-F2 and type in "gksu nautilus", it'll ask you for your password, then give you a file browser window.  Using this window, navigate to your cursors, extract them, copy them to wherever you like.

gksu is the graphical equivalent to the "sudo" command.  Both these commands follow the form "sudo <any other command>" and then said other command is run with root/administrator privileges.

The whole idea behind this scheme is to allow you to get write access to important areas of your system when you need it, but prevent you from messing up things with an accidental command.

Just for your own personal learning, here's a quick tutorial about the linux directory structure:
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)
Every folder except /tmp, /var, and /home/<your username> is going to be owned by root (i.e. you won't have access to write there unless you give it to yourself for that specific action)

Another thing that might be helpful to you is the "nautilus-gksu" package.  You can install it from synaptic (System->Administration->Synaptic)
It lets you right-click files/folders and open them as root/administrator.  So for example, let's say you have some zip file with cursors, with this package installed (you might need to restart after you install it) you can right click the zip, say "open as administrator" then when you tell it where to extract the files to, it will have root privileges and be able to do what you need.

---

### Post by mechanicforme on 2008-12-10
ok awesome i did that and i went to appearance and then pointer and i dont see it in there?

---

### Post by mechanicforme on 2008-12-11
?

---

