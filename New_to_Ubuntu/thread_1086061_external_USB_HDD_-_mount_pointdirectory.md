---
title: "external USB HDD - mount point/directory"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by capnthommo on 2009-03-03
hi everybody.
i have an external USB HDD formatted to ext3.  i am a little confused.
when i connect it it lists (in eg system monitor) as /dev/sdb1 and its directory is /media/disk.  it also shows in 'Places; as '640.1GB Media' and
when i connect it i get the pop-up notifying me that 
[you have just inserted a picture cd. choose what application...]
it clearly is not a picture cd so what is happening here?
how can i get it to come up as for example /HDD 
BTW it behaves as i would expect it to - it accepts rsync backups and so-on and has word processor/spreadsheet files on it so?
oh, and it also shows on conky as /disk
cheers for any help
nigel

---

### Post by llamabr on 2009-03-03
Hi.  No idea.  If you don't get any replies, you might think about taking this question to the appropriate forum.  I think there's one for peripherals up there.

Good luck.

---

### Post by cjv8888 on 2009-03-03
> **capnthommo said:**
> hi everybody.
i have an external USB HDD formatted to ext3.  i am a little confused.
when i connect it it lists (in eg system monitor) as /dev/sdb1 and its directory is /media/disk.  it also shows in 'Places; as '640.1GB Media' and
when i connect it i get the pop-up notifying me that 
[you have just inserted a picture cd. choose what application...]
it clearly is not a picture cd so what is happening here?
how can i get it to come up as for example /HDD 
BTW it behaves as i would expect it to - it accepts rsync backups and so-on and has word processor/spreadsheet files on it so?
oh, and it also shows on conky as /disk
cheers for any help
nigel

You can rename the USB drive using this [guide.]("https://help.ubuntu.com/community/RenameUSBDrive")

or if you are using KDE desktop, I think you can rename it directly at the menu level.

---

### Post by capnthommo on 2009-03-03
ok thanks there guys
i have followed the instructions and renamed the drive so it shows as something more appropriate.
but it still thinks it's a picture CD for some reason.  i followed the sub link but the instructions to 'change the mount point' leave me a little confused.  can anyone help further?  
it doesn't seem too important but i would like to tidy it up if possible.
oh, and if somebody wants to move it to a more appriopriate section please feel free.
cheers
nigel

---

### Post by erudite on 2009-03-03
After doing a search I found that if you have a folder called pictures on the first level Intrepid believes it to be a picture CD.  Prehaps if you renamed or moved this folder which I assume you have, you would be ok.

[LINK]("http://ubuntuforums.org/showthread.php?t=969897")

---

### Post by capnthommo on 2009-03-04
ok thanks everybody.
i changed the name of the 'pictures' folder and now the message has gone away and all is normal.
thanks for that.
nigel

---

### Post by erudite on 2009-03-04
Your welcome mate.  Feel free to mark this thread as solved now in thread tools.

Thanks.

---

