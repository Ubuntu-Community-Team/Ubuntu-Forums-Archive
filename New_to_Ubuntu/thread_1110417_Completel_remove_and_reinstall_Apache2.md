---
title: "Completel remove and reinstall Apache2"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-03-29
OK. I did it. Was trying to set up Apache to use as a local web server to go to a drive in the user root instead of /var/www and managed to get completely confused. Removed Apache via the Synaptics package removal and then installed it with the Synaptics install. Now I get "Forbidden" when I go to local host. Before I messed with it I did get the message "IT WORKS". So I did it. My fault.

Now, what is the proper way to remove it ad then reinstall Apache so I get back to the normal defaults?  While I can replace the entire partition and then redo Fstab and the boot menu I would prefer to fix it as a learning exercise. So where do I start?

---

### Post by 123456789123456789123456 on 2009-03-29
go to synaptics package removal, right click on Apache, go down to completely remove.  This will tell the computer to completely uninstall the program, and delete all old installation files used to install it.  When you go to install it, Ubuntu will have to download the files again, configure and install from scratch.

---

### Post by snova on 2009-03-29
Configuration files are contained in the apache2.2-common package, so purging this and reinstalling it should work. (There might be a more direct way, but I don't know of it.)

I think Synaptic can do it, via the "Mark for complete removal" option.

---

### Post by Al Fischer on 2009-03-29
OK. I will try both things. I was unaware of the 'right click' approach. Sounds like what I was looking for. Thanks and I will report back the results.

---

### Post by Al Fischer on 2009-03-30
That did it. I should have thought of the right click. 

THANK YOU!

Now back to the adventure with seting up my server.Lots to learn.

---

