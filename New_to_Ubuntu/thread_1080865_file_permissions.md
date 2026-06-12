---
title: "file permissions"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by kyeh on 2009-02-25
I have a shared folder which anybody can read/write to, however when someone puts files into the folder, the permissions are set that only that user can read it, is there a way to make it readable/writeable to everyone by default?

---

### Post by llamabr on 2009-02-25
Look into the utility called umask, but don't read the man page.

---

### Post by iaculallad on 2009-02-25
Try changing the folders permission using terminal command chmod:

```
sudo chmod -R 777 /mount_point/folder_name
```

---

### Post by Miljet on 2009-02-26
Permissions given to a file or directory are assigned originally at the time that file or directory is created. How these permissions are set is based on the user's current umask value.

The umask value is set in /etc/profile and the default is 022 which makes files -rw-r--r--. Changing that to 000 will make any files -rw-rw-rw-.

Please bear in mind that if you do this, ALL files will be created with these permissions, not just the ones created in your public folder.

For more information see this link. [http://www.tech-faq.com/umask.shtml](http://www.tech-faq.com/umask.shtml)

There is probably a better way to do what you want, but this is a start.

---

### Post by myddewji13 on 2009-02-26
You could always install ubuntu tweak... under System-->Nautilus you can enable advanced use permissions...then right click folder/file to modify...

---

