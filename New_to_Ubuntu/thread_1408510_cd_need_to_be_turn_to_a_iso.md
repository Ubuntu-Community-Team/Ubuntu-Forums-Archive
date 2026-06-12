---
title: "cd need to be turn to a iso"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by ibizatunes on 2010-02-16
Hello, 
I have a Redhat 4u6 DVD, that work fine, i need to change the kickstart as im building some servers tomorrow, i have the new kick start and have copied the data to my harddrive, keeping the permission the same + hidden file etc
But im struggling to recreate .ISO file with the change with the new kickstart in it
I can create the ISO but it doesn't seem to boot, or in vmware player doesnt recognize the OS
PLEASE HELP!!

---

### Post by bodhi.zazen on 2010-02-16
[http://www.ibm.com/developerworks/linux/library/l-fedora-livecd/](http://www.ibm.com/developerworks/linux/library/l-fedora-livecd/)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by ibizatunes on 2010-02-16
I was over complicating the issue, all my fault, long day i guess! i forgot how amazing ubuntu is, i cp -rp * my cd drive over to my harddrive, if i had used Brasero, and saved the CD as a .iso image then used a iso editor (iso master) to remaster it i would have been sorted alot quicker
Silly silly boy! 
Thanks for you help

---

### Post by Charlietje on 2010-02-16
is that what you want:
```

mkisofs -o iso_path/to/iso_name.iso path/to/directory_of_files_to_brun

```

---

