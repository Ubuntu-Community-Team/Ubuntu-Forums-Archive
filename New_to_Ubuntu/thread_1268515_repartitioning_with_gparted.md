---
title: "repartitioning with gparted"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by davidwroe on 2009-09-17
Hi Im new to Ubuntu (using 9.4) and I have a dual boot with vista. I am trying to reduce the size of the Linux partition with gparted activated from the system/admin menu (partition editor) .I see all partitions (vista included) but dont seem to have an option to resize the one containing Ubuntu.  Help appreciated - please  note I AM an absolute beginner with linux - dont even know what a 'flag'is yet

---

### Post by kiridude on 2009-09-17
The partition you want to resize must be unmounted. Best way to proceed is to use the live cd, that way all partitions will be unmounted.

---

### Post by theozzlives on 2009-09-17
You'll have to use the live CD as your partitions are in use if you do it off the hard drive

---

### Post by mapes12 on 2009-09-17
Hi and welcome to the forum.

If you're dual booting then take a look at this excellent resource: 

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by nhasian on 2009-09-17
no one has mentioned this yet, but if your going to resize partitions, [COLOR="Red"]back up your data first![/COLOR] in case of any program or user error...

---

### Post by mike555 on 2009-09-17
Parted Magic live cd is good for doing this and other stuff (like cloning ,etc)......   [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by mikechant on 2009-09-17
Even when using the liveCD, your swap partition will still be in use.

Depending on your partition layout this may prevent you resizing your main Ubuntu partition.

So when you go into Gparted from the LiveCD, right click on the swap partition and select 'swapoff' before you do anything else.

If you're confused, post a screen shot of Gparted and we'll tell you exactly what needs doing.

---

### Post by davidwroe on 2009-09-17
thanx but I have no idea how to post a screen shot?????

---

### Post by Penguin Guy on 2009-09-17
> **davidwroe said:**
> thanx but I have no idea how to post a screen shot?????
You press the [button with 'Print Screen' written on it]("http://ubuntuforums.org/attachment.php?attachmentid=128896&stc=1&d=1253204659").

---

### Post by davidwroe on 2009-09-18
Thanx for all help offered.  Partition now resized with gparted.  Have formatted it with ntfs for use with windows vista but cannot move the partition?   What am I not doing??

---

### Post by kiridude on 2009-09-18
Post a screen shot of your gparted. That way we can have a better idea of what your setup is and what you want to do.

---

### Post by mapes12 on 2009-09-19
> **davidwroe said:**
> Thanx for all help offered.  Partition now resized with gparted.  Have formatted it with ntfs for use with windows vista but cannot move the partition?   What am I not doing??I don't use Vista myself but I read somewhere that it was not recommended to move Vista partitions with GParted. I don't know the reason but the post said that there is a partitioning tool built into Vista that should be used on Vista partitions. This might be your problem. I found this bunch of info: [http://www.google.co.uk/#hl=en&source=hp&q=vista+partition&meta=&aq=0&oq=vista+par&fp=65a6334453af9707](http://www.google.co.uk/#hl=en&source=hp&q=vista+partition&meta=&aq=0&oq=vista+par&fp=65a6334453af9707)

---

