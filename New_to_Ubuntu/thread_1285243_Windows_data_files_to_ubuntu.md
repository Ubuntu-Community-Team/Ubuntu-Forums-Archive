---
title: "Windows data files to ubuntu"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by steel.knee on 2009-10-07
Sucessfully installed ubunta beside Vista on my laptop. Now how do I get things like documents and bookmarks from the Visa side to Ubunta side. I was alreadt using Firefox and OpenOffice on Vista, should would like to transfer data files to Ubunta applications.

---

### Post by CaptainMark on 2009-10-07
ubuntu wont automatically mount windows filesystems but it can easily be done, post the output from ```
sudo fdisk -l
```

---

### Post by ikisham on 2009-10-07
You click on 'Places' at the top panel and then 'Computer'.
It'll show some disks. You just click on the one that has Vista installed and it will open normal.

---

### Post by yknivag on 2009-10-07
If you go to the "Places" menu you'll see an icon of a hard drive with the legend "xxGB Media".  Click that and it will the partition automatically and you'll be able to read/write your files.

If that doesn't work, then you may need to go to "System"->"Applications"->"Synaptic Package Manager" and search for and install a package called "ntfs-3g" and try again.

---

