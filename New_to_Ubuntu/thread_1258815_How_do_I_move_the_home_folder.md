---
title: "How do I move the home folder?"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Seithe on 2009-09-05
How do I move my home folder to a different location?

---

### Post by wojox on 2009-09-05
Where do you want to move it to? 

A different partition?

It's not recommended to move it anywhere else in the system.

---

### Post by halitech on 2009-09-05
If you want to create a seperate /home after installing with /home inside / there are directions here

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Seithe on 2009-09-05
I wanted to move it to the "/media/disk" which seems to permenate on my computer and it can't be deleted. Well I only want to move it in here because thats where all my free space ended up and I don't know why so I was thinking about moving my home into it so I can have some free space back on my computer since that is where all my free space is.

---

### Post by achianese on 2009-09-05
Presumably, /media/disk is another partition that you have.. possibly an NTFS partition containing Windows?

If this is indeed another OS, you might not want to make it your primary data directory, but you could simply put a symbolic link in your home folder that leads to a folder in media/disk. In a terminal:

```
cd ~
ln -s /media/disk/FOLDERNAME NAMEOFLINK
```

If the partition at /media/disk is empty or you don't mind reformatting it, you could do that and follow the instructions in halitech's post to move home there.

---

### Post by Seithe on 2009-09-05
Do I need the the Live CD to do this?

---

### Post by Copernicus1234 on 2009-09-05
Nope. Just run the above commands in a terminal and you will have a soft link on the file system to the folder.

You probably will need to type "sudo" ahead of the command to run it as root (Administrator).

---

### Post by halitech on 2009-09-05
to follow achianese's instructions no. to follow the instructions in the link I provided then yes.

---

